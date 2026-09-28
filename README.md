# Trao Quach - Academic Research Notes

Personal academic website and daily research publishing hub built with [Hugo Blox](https://hugoblox.com) and hosted on **GitHub Pages**, managed effortlessly via **Decap CMS**.

## 🚀 Live Site
- Website: **[https://traoquach.github.io/academic-notes/](https://traoquach.github.io/academic-notes/)**
- Web Admin CMS: **[https://traoquach.github.io/academic-notes/admin/](https://traoquach.github.io/academic-notes/admin/)**

## 🛠 Tech Stack
- **Static Site Generator:** [Hugo](https://gohugo.io/) (Extended Edition)
- **Theme Framework:** [Hugo Blox Builder](https://hugoblox.com) (Bootstrap v5 Academic Module)
- **Deployment:** GitHub Actions to GitHub Pages
- **CMS:** [Decap CMS](https://decapcms.org/) (formerly Netlify CMS)
- **Math Engine:** KaTeX / MathJax LaTeX rendering
- **Topics:** Federated Learning, Deep Learning, Human Activity Recognition, Edge AI

## 📝 Daily Publishing Workflow

### Option 1: Web Interface (Decap CMS)
1. Go to `https://traoquach.github.io/academic-notes/admin/`
2. Sign in with your GitHub account
3. Click **New Daily Research Note**
4. Type your research insights with full Markdown and LaTeX support: `$$ \min_w f(w) $$`
5. Click **Publish** -> GitHub Actions automatically builds and deploys to GitHub Pages in ~45 seconds!

### Option 2: Terminal / Command Line
```bash
# Create a new research note
hugo new post/$(date +%Y-%m-%d)-research-idea/index.md

# Start local server to preview
hugo server -D

# Commit and push to main branch
git add .
git commit -m "feat: daily research note on federated HAR"
git push origin main
```

## ⚙️ GitHub Pages Setup Check
1. Go to your GitHub repository -> **Settings** -> **Pages**
2. Under **Build and deployment** > **Source**, select **GitHub Actions**
3. Push to `main` and check the **Actions** tab!
