# Claude Go-To

An original, static learning website for building dependable AI-assisted development workflows. It is designed to publish directly to GitHub Pages with no build step or hosting bill.

## Publish it under your GitHub account

1. Create a new **public** repository called `claude-go-to` in your GitHub account.
2. Edit [site-config.js](site-config.js), replacing `YOUR_GITHUB_USERNAME` and the example email.
3. Add these files to the repository and push the `main` branch.
4. In GitHub, open **Settings → Pages**, choose **GitHub Actions** as the source, and wait for the included workflow to finish.
5. Your website will be available at:

   `https://YOUR_GITHUB_USERNAME.github.io/claude-go-to/`

The repository includes [a GitHub Pages workflow](.github/workflows/deploy-pages.yml). It runs whenever you push to `main`.

## Personalization checklist

- [ ] Update the GitHub username, site URL, and contact email in `site-config.js`.
- [ ] Replace the title and description in `index.html` if your audience needs a more specific focus.
- [ ] Change the guide content in `guides/` to match your team’s tools and conventions.
- [ ] Add your GitHub username to the footer automatically via the config file.
- [ ] Use a custom domain only after setting its DNS and GitHub Pages configuration.

## Local preview

Open `index.html` in a modern browser. Because this site only uses HTML, CSS, and vanilla JavaScript, it does not need npm or a server to work.

## Naming and intellectual-property note

All website code and written guide content in this repository are original. The project was independently built after being inspired by the learning-path idea in [luongnv89/claude-howto](https://github.com/luongnv89/claude-howto), which is MIT-licensed. See [NOTICE.md](NOTICE.md) for attribution.

`Claude` is a trademark of Anthropic. This is an unofficial educational project; it is not affiliated with, endorsed by, or sponsored by Anthropic. Do not use Anthropic logos or present the project as official.

## License

Claude Go-To is provided under the [MIT License](LICENSE).
