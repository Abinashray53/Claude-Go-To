# GitHub publishing checklist

This project is ready for GitHub Pages. It deliberately uses a placeholder because the GitHub account and target repository were not provided:

- `YOUR_GITHUB_USERNAME`
- `https://github.com/YOUR_GITHUB_USERNAME/claude-go-to`
- `https://YOUR_GITHUB_USERNAME.github.io/claude-go-to/`

## Option A — GitHub website (no Git installation needed)

1. Sign in to GitHub and create a **public** repository named `claude-go-to`.
2. Open [site-config.js](site-config.js) and replace the placeholders with your username, final site address, and public contact email.
3. In the new repository, select **Add file → Upload files**.
4. Upload everything in this folder, including the hidden `.github` folder and `.nojekyll` file.
5. Commit to the `main` branch.
6. Open **Settings → Pages** and set **Build and deployment** to **GitHub Actions**.
7. Open the **Actions** tab and wait for “Deploy static site to GitHub Pages” to complete.

## Option B — Git command line

After installing Git, run these commands from this folder:

```powershell
git init
git add .
git commit -m "Initial Claude Go-To site"
git branch -M main
git remote add origin https://github.com/YOUR_GITHUB_USERNAME/claude-go-to.git
git push -u origin main
```

Then enable **GitHub Actions** in **Settings → Pages** as described above.

## Before you publish

- Keep [NOTICE.md](NOTICE.md) and [LICENSE](LICENSE) in the repository.
- Keep the unofficial-project disclaimer in the footer.
- Do not use Anthropic’s logo or claim an official relationship.
- Replace the example contact email before public deployment.
