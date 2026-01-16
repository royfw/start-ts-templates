# docs-docsify

A lightweight documentation site template powered by [Docsify](https://docsify.js.org/). Perfect for creating beautiful documentation websites without the need for build processes or static site generation.

## ✨ Features

- 📝 **Zero Build** - No static site generation, runs directly in browser
- 🎨 **Beautiful Themes** - Multiple themes and customization options
- 🔍 **Full-text Search** - Built-in search functionality
- 📱 **Responsive** - Mobile-friendly design
- ⚡ **Fast** - Instant page loading
- 🌐 **i18n Ready** - Multi-language support
- 🔌 **Plugin System** - Rich ecosystem of plugins
- 📦 **Easy Deploy** - Deploy to GitHub Pages, Netlify, or any static host

## 🚀 Quick Start

```bash
# Install dependencies
pnpm install

# Start development server
pnpm dev

# Build for production (if using custom build)
pnpm build

# Run tests
pnpm test
```

## 📖 Documentation

For complete documentation, see:
- [English Documentation](./docs/README.md)
- [繁體中文文檔](./docs/README.zh-TW.md)

## 🛠️ Development Scripts

```bash
# Development
pnpm dev          # Start with esbuild (if applicable)
pnpm dev:esbuild  # esbuild watch mode
pnpm dev:rollup   # Rollup watch mode

# Build
pnpm build        # Production build

# Testing
pnpm test         # Run unit tests
pnpm test:e2e     # Run E2E tests
pnpm jest:cov     # Coverage report

# Code Quality
pnpm lint         # Check code style
pnpm lint:fix     # Fix issues
```

## 📁 Project Structure

```
docs-docsify/
├── docs/                    # Documentation content
│   ├── README.md           # Homepage
│   ├── guide/              # Guide pages
│   └── _sidebar.md         # Sidebar navigation
├── src/                    # Custom scripts (if needed)
└── index.html              # Docsify entry point
```

## 🌐 Live Preview

Once started, access the documentation at:
- **Documentation**: `http://localhost:3000`

## 🔧 Tech Stack

- **Runtime**: Node.js 18+
- **Framework**: Docsify (client-side)
- **Language**: TypeScript 5.7+
- **Build Tool**: esbuild 0.25+ / Rollup 4.36+
- **Testing**: Jest 29.7+
- **Package Manager**: pnpm 10.24+

## 📄 License

ISC

---

**Created with** [start-ts-templates](https://github.com/royfw/start-ts-templates)

For more templates, check out the [template collection](https://github.com/royfw/start-ts-templates/tree/main/templates).