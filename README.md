"""
==================================================
 GitHub Profile README Generator (Professional)
==================================================
Author: Your Name
Description:
    Generates a clean, stylish, and well-categorized
    GitHub profile README.md using user input.

Usage:
    python github_profile_readme_generator.py
==================================================
"""

# -----------------------------
# README TEMPLATE GENERATOR
# -----------------------------
def generate_readme(user):
    return f"""
<h1 align="center">Hi 👋, I'm {user['name']}</h1>
<h3 align="center">{user['headline']}</h3>

<p align="center">
  <img src="https://komarev.com/ghpvc/?username={user['username']}&label=Profile%20Views&color=0e75b6&style=flat" />
</p>

---

## 🧑‍💻 About Me
- 🎓 **Education:** {user['education']}
- 💼 **Role:** {user['role']}
- 🌱 **Currently Learning:** {user['learning']}
- 🎯 **Interests:** {user['interests']}

---

## 🛠️ Technical Skills

### 👨‍💻 Programming Languages
{user['languages']}

### ⚙️ Tools & Platforms
{user['tools']}

### 📚 Core Concepts
{user['concepts']}

---

## 📂 Featured Projects
{user['projects']}

---

## 📊 GitHub Statistics
<p align="center">
  <img src="https://github-readme-stats.vercel.app/api?username={user['username']}&show_icons=true&theme=tokyonight" />
</p>

<p align="center">
  <img src="https://github-readme-streak-stats.herokuapp.com/?user={user['username']}&theme=tokyonight" />
</p>

<p align="center">
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username={user['username']}&layout=compact&theme=tokyonight" />
</p>

---

## 🤝 Connect With Me
<p align="left">
  <a href="https://github.com/{user['username']}">
    <img src="https://img.shields.io/badge/GitHub-181717?style=flat&logo=github&logoColor=white"/>
  </a>
</p>

---

⭐ *Thanks for visiting my profile! Feel free to explore my repositories and connect.*
"""


# -----------------------------
# HELPER FUNCTIONS
# -----------------------------
def badge_list(items, color):
    """
    Converts comma-separated values into badge-style markdown
    """
    badges = []
    for item in items.split(","):
        item = item.strip()
        badges.append(
            f"- ![Badge](https://img.shields.io/badge/{item.replace(' ', '%20')}-{color}?style=flat)"
        )
    return "\n".join(badges)


def bullet_list(items, emoji):
    """
    Converts comma-separated values into emoji bullet list
    """
    return "\n".join([f"- {emoji} {i.strip()}" for i in items.split(",")])


# -----------------------------
# MAIN PROGRAM
# -----------------------------
def main():
    print("\n🚀 GitHub Profile README Generator (Professional Edition)\n")

    user = {}
    user["name"] = input("Full Name: ")
    user["headline"] = input("Profile Headline (e.g. Aspiring Software Developer): ")
    user["education"] = input("Education: ")
    user["role"] = input("Current Role: ")
    user["learning"] = input("Currently Learning: ")
    user["interests"] = input("Interests: ")
    user["username"] = input("GitHub Username: ")

    print("\n--- Skills Section ---")
    user["languages"] = badge_list(
        input("Programming Languages (comma-separated): "),
        "blue"
    )

    user["tools"] = badge_list(
        input("Tools & Platforms (comma-separated): "),
        "orange"
    )

    user["concepts"] = bullet_list(
        input("Core Concepts (comma-separated): "),
        "📌"
    )

    print("\n--- Projects Section ---")
    print("Enter project titles (type 'done' to finish):")
    projects = []
    while True:
        p = input("- ")
        if p.lower() == "done":
            break
        projects.append(f"- 🚀 **{p}**")

    user["projects"] = "\n".join(projects)

    # Write README.md
    with open("README.md", "w", encoding="utf-8") as file:
        file.write(generate_readme(user))

    print("\n✅ README.md generated successfully!")
    print("📌 Upload it to a repository named exactly your GitHub username.")


# -----------------------------
# ENTRY POINT
# -----------------------------
if __name__ == "__main__":
    main()
