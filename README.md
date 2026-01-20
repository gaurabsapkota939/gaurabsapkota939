"""
Stylish GitHub Profile README Generator
Creates a modern, badge-based, visually appealing README.md
"""

def generate_readme(d):
    return f"""
<h1 align="center">Hi 👋, I'm {d['name']}</h1>
<h3 align="center">{d['tagline']}</h3>

<p align="center">
  <img src="https://komarev.com/ghpvc/?username={d['github']}&label=Profile%20views&color=0e75b6&style=flat" alt="{d['github']}" />
</p>

---

## 🙋‍♂️ About Me
- 🎓 {d['education']}
- 💻 {d['role']}
- 🌱 Currently learning **{d['learning']}**
- 🎯 Interested in **{d['interests']}**

---

## 🛠️ Tech Stack
![Languages](https://img.shields.io/badge/Languages-{d['languages']}-informational?style=flat&logo=code)
![Tools](https://img.shields.io/badge/Tools-{d['tools']}-blue?style=flat&logo=tools)
![Concepts](https://img.shields.io/badge/Concepts-{d['concepts']}-success?style=flat&logo=book)

---

## 📂 Featured Projects
{d['projects']}

---

## 📊 GitHub Stats
<p align="center">
  <img src="https://github-readme-stats.vercel.app/api?username={d['github']}&show_icons=true&theme=tokyonight" />
</p>

<p align="center">
  <img src="https://github-readme-streak-stats.herokuapp.com/?user={d['github']}&theme=tokyonight" />
</p>

---

## 🤝 Connect With Me
<p align="left">
<a href="https://github.com/{d['github']}" target="_blank">
  <img src="https://img.shields.io/badge/GitHub-181717?style=flat&logo=github&logoColor=white" />
</a>
</p>

---

⭐ *Thanks for visiting my profile! Feel free to explore my repositories.*
"""


def main():
    print("✨ Stylish GitHub Profile README Generator ✨\n")

    d = {
        "name": input("Your full name: "),
        "tagline": input("Short tagline (e.g. Aspiring Software Developer): "),
        "education": input("Education: "),
        "role": input("Current role: "),
        "learning": input("Currently learning: "),
        "interests": input("Main interests: "),
        "languages": input("Languages (C#, Java, etc.): ").replace(" ", "%20"),
        "tools": input("Tools (Git, VS Code, etc.): ").replace(" ", "%20"),
        "concepts": input("Concepts (OOP, UML, etc.): ").replace(" ", "%20"),
        "github": input("GitHub username: "),
    }

    print("\nEnter projects (type 'done' to finish):")
    projects = []
    while True:
        p = input("- ")
        if p.lower() == "done":
            break
        projects.append(f"- 🚀 {p}")

    d["projects"] = "\n".join(projects)

    with open("README.md", "w", encoding="utf-8") as f:
        f.write(generate_readme(d))

    print("\n✅ Stylish README.md generated successfully!")


if __name__ == "__main__":
    main()
