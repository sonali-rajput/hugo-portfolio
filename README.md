# Sonali Rajput's Portfolio

Personal portfolio website built with Hugo and the Archie theme.

## 🚀 Quick Start

```bash
# Clone the repository
git clone https://github.com/username/sonali-portfolio.git
cd sonali-portfolio

# Start the development server
hugo server -D

# Build for production
hugo --minify
```

## 📦 Deployment

This site is automatically deployed to GitHub Pages using GitHub Actions.

### Setup Instructions:

1. **Fork this repository** to your GitHub account
2. **Update the repository name** to `sonali-portfolio` (or your preferred name)
3. **Update hugo.toml**:
   - Change `baseURL` to your GitHub Pages URL or custom domain
4. **Enable GitHub Pages**:
   - Go to Settings → Pages
   - Select "GitHub Actions" as the source
5. **Push your changes** - the site will build automatically!

### Custom Domain (Optional):

If you want to use a custom domain like `heyiamsra.com`:

1. **Add your domain** to the `static/CNAME` file
2. **Configure DNS** at your domain provider to point to GitHub Pages
3. **Enable custom domain** in GitHub Pages settings

## 🛠️ Tech Stack

- **Hugo** - Static site generator
- **Archie Theme** - Minimal, clean theme
- **GitHub Pages** - Hosting
- **GitHub Actions** - CI/CD

## 📁 Structure

```
├── content/
│   ├── _index.md          # Home page
│   ├── experience/        # Experience page
│   ├── projects/          # Projects section
│   ├── certifications/    # Certifications
│   ├── contact/           # Contact info
│   └── posts/             # Blog posts
├── static/
│   ├── images/            # Images
│   └── CNAME              # Custom domain
├── layouts/               # Custom layouts
└── hugo.toml              # Hugo configuration
```

## 🎨 Customization

- **Colors & Styling**: Modify the Archie theme in `themes/archie/`
- **Navigation**: Edit the menu in `hugo.toml`
- **Content**: Add new pages in `content/`
- **Images**: Place images in `static/images/`

## 📝 Adding Content

### New Blog Post:
```bash
hugo new posts/my-new-post.md
```

### New Project:
```bash
hugo new projects/my-project.md
```

## 🔧 Development

```bash
# Install Hugo (macOS)
brew install hugo

# Install Hugo (Linux)
sudo apt install hugo

# Start development server
hugo server -D --bind 0.0.0.0 --baseURL http://localhost:1313
```

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

---

Built with ❤️ by [Sonali Rajput](https://heyiamsra.com)