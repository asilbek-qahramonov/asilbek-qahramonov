<h1 align="center">
  <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=700&size=36&duration=3000&pause=800&color=00C9FF&center=true&vCenter=true&width=600&height=70&lines=Hi+%F0%9F%91%8B+I'm+Asilbek;Frontend+Developer;UI+Builder;JavaScript+Enthusiast" alt="Typing SVG" />
</h1>

<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:00C9FF,100:92FE9D&height=200&section=header&text=Asilbek%20Qahramonov&fontSize=40&fontColor=ffffff&animation=fadeIn&fontAlignY=38&desc=Frontend%20Developer%20%7C%20UI%20Builder&descAlignY=58&descSize=18" alt="Header" />
</p>

---

## 💻 Tech Stack

<p align="center">
  <img src="https://skillicons.dev/icons?i=html,css,tailwind,bootstrap,js,react,python,git,github,vscode,figma&theme=dark" alt="Tech Stack" />
</p>

<p align="center">
  <img src="https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white" alt="HTML5" />
  <img src="https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white" alt="CSS3" />
  <img src="https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white" alt="Tailwind" />
  <img src="https://img.shields.io/badge/Bootstrap-563D7C?style=for-the-badge&logo=bootstrap&logoColor=white" alt="Bootstrap" />
  <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black" alt="JavaScript" />
  <br/>
  <img src="https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB" alt="React" />
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python" />
  <img src="https://img.shields.io/badge/Telegram_Bot-26A5E4?style=for-the-badge&logo=telegram&logoColor=white" alt="Telegram Bot" />
  <img src="https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white" alt="Java" />
  <br/>
  <img src="https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white" alt="Git" />
  <img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white" alt="GitHub" />
  <img src="https://img.shields.io/badge/VS_Code-007ACC?style=for-the-badge&logo=visual-studio-code&logoColor=white" alt="VS Code" />
  <img src="https://img.shields.io/badge/Figma-F24E1E?style=for-the-badge&logo=figma&logoColor=white" alt="Figma" />
</p>

---

<!-- 3D Contribution Snake -->
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/platane/snk/output/github-contribution-grid-snake-dark.svg" />
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/platane/snk/output/github-contribution-grid-snake.svg" />
  <img alt="github-snake" src="https://raw.githubusercontent.com/platane/snk/output/github-contribution-grid-snake-dark.svg" width="100%" />
</picture>


---


# gh-space-shooter 🚀

Transform your GitHub contribution graph into an epic space shooter game! 

![Example Game](example.gif)

## Usage

### Onetime Generation

A [web interface](https://gh-space-shooter.kiyo-n-zane.com) is available for on-demand GIF generation without installing anything locally. 

### GitHub Action

Automatically update your game GIF daily using GitHub Actions! Add this workflow to your repository at `.github/workflows/update-game.yml`:

```yaml
name: Update Space Shooter Game

on:
  schedule:
    - cron: '0 0 * * *'  # Daily at midnight UTC
  workflow_dispatch:  # Allow manual trigger

permissions:
  contents: write

jobs:
  update-game:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - uses: czl9707/gh-space-shooter@v1
        with:
          github-token: ${{ secrets.GITHUB_TOKEN }}
          output-path: 'game.gif'
          # write-dataurl-to: 'README.md'   # for dataurl generation.
          strategy: 'random'
```

Then display it in your README:
```markdown
![My GitHub Game](game.gif)
```

**Action Inputs:**
- `github-token` (required): GitHub token for fetching contributions
- `username` (optional): Username to generate game for (defaults to repo owner)
- `output-path` (optional): Where to save the animation, supports `.gif` or `.webp` (default: `gh-space-shooter.gif`)
- `strategy` (optional): Attack pattern - `column`, `row`, or `random` (default: `random`)
- `fps` (optional): Frames per second for the animation (default: `40`)
- `write-dataurl-to` (optional): Write WebP as HTML `<img>` data URL to text file
- `commit-message` (optional): Commit message for the update

### From PyPI

```bash
pip install gh-space-shooter
```

### From Source

```bash
# Clone the repository
git clone https://github.com/yourusername/gh-space-shooter.git
cd gh-space-shooter

# Install with uv
uv sync

# Or with pip
pip install -e .
```

## Setup

1. Create a GitHub Personal Access Token:
   - Go to https://github.com/settings/tokens
   - Click "Generate new token (classic)"
   - Select scopes: `read:user`
   - Copy the generated token

2. Set up your environment:
   ```bash
   # Copy the example env file
   touch .env
   echo "GH_TOKEN=your_token_here" >> .env
   ```

   Alternatively, export the token directly:
   ```bash
   export GH_TOKEN=your_token_here
   ```

## CLI Usage

### Generate Your Game Animation (GIF or WebP)

Transform your GitHub contributions into an epic space shooter!

```bash
# Basic usage - generates username-gh-space-shooter.gif
gh-space-shooter <username>

# Examples
gh-space-shooter torvalds
gh-space-shooter octocat

# Specify custom output filename (GIF or WebP)
gh-space-shooter torvalds --output my-epic-game.gif
gh-space-shooter torvalds -o my-game.webp

# Choose enemy attack strategy
gh-space-shooter torvalds --strategy row      # Enemies attack in rows
gh-space-shooter torvalds -s random           # Random chaos (default)

# Adjust animation frame rate
gh-space-shooter torvalds --fps 25            # Lower Frame rate, Smaller file size
gh-space-shooter torvalds --fps 40            # Default Frame rate, Larger file size

# Stop the animation earlier
gh-space-shooter torvalds --max-frame 200     # Stop after 200 frames
```

This creates an animated GIF showing:
- Your contribution graph as enemies (more contributions = stronger enemies)
- A Galaga-style spaceship battling through your coding history
- Enemy attack patterns based on your chosen strategy
- Smooth animations with randomized particle effects
- Your contribution stats displayed in the console

### Generate Data URL (for embedding in HTML/Markdown)

For direct embedding in READMEs or HTML files, use `--write-dataurl-to` to generate a WebP data URL wrapped in an HTML `<img>` tag:

> Note: This not necessarily will work. The .webp can grow over 1 MB very easily, which github will just refuse to render.

```bash
# Generate data URL and write to README.md
gh-space-shooter torvalds --write-dataurl-to README.md

# Short form
gh-space-shooter torvalds -wdt README.md
```

**Using section markers:** To use this feature, add section markers to your file where you want the game to appear:

```markdown
# My Profile

<!--START_SECTION:space-shooter-->
<!--END_SECTION:space-shooter-->

## About Me
```

This will:
- **Create new files** with content wrapped in section markers, if file not present.
- **Replace content** between existing markers (preserving surrounding content)
- **Raise error** if markers are missing or in wrong order (no silent fallback)

### Advanced Options

```bash
# Save raw contribution data to JSON
gh-space-shooter torvalds --raw-output data.json

# Load from previously saved JSON (saves API rate limits)
gh-space-shooter --raw-input data.json --output game.webp

# Combine options
gh-space-shooter torvalds -o game.webp -ro data.json -s column

# Generate data URL with custom strategy
gh-space-shooter torvalds -wdt README.md -s column
```

### Data Format

When saved to JSON, the data includes:
```json
{
  "username": "torvalds",
  "total_contributions": 1234,
  "weeks": [
    {
      "days": [
        {
          "date": "2024-01-01",
          "count": 5,
          "level": 2
        }
      ]
    }
  ]
}
```

## License

MIT


## 🚀 About Me

```python
class Asilbek:
    def __init__(self):
        self.name = "Qahramonov Asilbek"
        self.role = "Frontend Developer"
        self.location = "Uzbekistan"
        self.skills = ["HTML", "CSS", "Tailwind", "Bootstrap", "JavaScript", "React", "Python", "Telegram Bot"]
        self.interests = ["Modern UI", "Responsive Design", "Animations"]
        self.goal = "Building amazing web experiences"

    def say_hi(self):
        print("Building responsive and modern websites!")

me = Asilbek()
me.say_hi()
