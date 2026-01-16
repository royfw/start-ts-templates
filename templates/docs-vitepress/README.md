# docs-vitepress

A powerful documentation site template built with [VitePress](https://vitepress.dev/). Perfect for creating fast, SEO-friendly, and beautiful documentation websites with Vue 3 and Vite.

## ✨ Features

- ⚡ **Lightning Fast** - Powered by Vite for instant server start and HMR
- 🎨 **Beautiful Design** - Modern UI with customizable themes
- 🔍 **Built-in Search** - Local search with no extra dependencies
- 📱 **Responsive** - Mobile-optimized design
- 🌐 **i18n Ready** - First-class internationalization support
- 🎯 **Type-Safe** - Full TypeScript support
- 🚀 **SSG** - Static site generation for optimal performance
- 📦 **Easy Deploy** - Deploy to any static hosting service

## 🚀 Quick Start

```bash
# Install dependencies
pnpm install

# Start development server
pnpm docs:dev

# Build for production
pnpm docs:build

# Preview production build
pnpm docs:preview
```

## 📖 Documentation

For complete documentation, see:
- [English Documentation](./docs/README.md)
- [繁體中文文檔](./docs/README.zh-TW.md)

## 🛠️ Development Scripts

```bash
# Documentation
pnpm docs:dev      # Start VitePress dev server
pnpm docs:build    # Build documentation
pnpm docs:preview  # Preview production build

# Development (if using custom scripts)
pnpm dev           # Start with esbuild
pnpm build         # Production build

# Testing
pnpm test          # Run unit tests
pnpm test:e2e      # Run E2E tests

# Code Quality
pnpm lint          # Check code style
pnpm lint:fix      # Fix issues
```

## 📁 Project Structure

```
docs-vitepress/
├── docs/
│   ├── .vitepress/          # VitePress config
│   │   ├── config.ts        # Site configuration
│   │   └── theme/           # Custom theme
│   ├── index.md             # Homepage
│   ├── guide/               # Guide pages
│   └── api/                 # API reference
├── src/                     # Custom scripts (optional)
└── package.json
```

## 🌐 Live Preview

Once started, access the documentation at:
- **Documentation**: `http://localhost:5173`

## 🔧 Tech Stack

- **Runtime**: Node.js 18+
- **Framework**: VitePress 1.6+
- **Language**: TypeScript 5.7+
- **Build Tool**: Vite / esbuild 0.25+ / Rollup 4.36+
- **Testing**: Vitest 3.2+ / Jest 29.7+
- **Package Manager**: pnpm 10.24+

## 📄 License

ISC

---

**Created with** [start-ts-templates](https://github.com/royfw/start-ts-templates)

For more templates, check out the [template collection](https://github.com/royfw/start-ts-templates/tree/main/templates).