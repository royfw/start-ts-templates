# lib-esbuild

A high-performance TypeScript library template built with esbuild for ultra-fast compilation and bundling.

## ✨ Features

- **⚡ Ultra-Fast Builds** - esbuild provides 10-100x faster builds than traditional bundlers
- **📦 Dual Output** - ESM and CJS formats for maximum compatibility
- **🔷 TypeScript** - Full TypeScript support with type declarations
- **✅ Testing Ready** - Vitest configured for unit and E2E testing
- **📝 Code Quality** - ESLint, Prettier, Husky, and lint-staged pre-configured
- **🚀 CI/CD Ready** - GitHub Actions and GitLab CI examples included

## 🚀 Quick Start

```bash
# Install dependencies
pnpm install

# Development with watch mode
pnpm dev

# Build for production
pnpm build

# Run tests
pnpm test
```

## 📁 Project Structure

```
lib-esbuild/
├── src/
│   ├── index.ts              # Library entry point
│   └── utils/                # Utility functions
├── dist/                     # Build output
│   ├── index.js             # CJS bundle
│   ├── index.mjs            # ESM bundle
│   └── index.d.ts           # Type declarations
├── esbuild.build.ts         # Build configuration
└── package.json             # Package configuration
```

## 📚 Documentation

For detailed documentation, see [docs/README.md](./docs/README.md) or [繁體中文文檔](./docs/README.zh-TW.md).

## 🛠️ Tech Stack

- **Build Tool**: esbuild 0.25+
- **Language**: TypeScript 5.7+
- **Testing**: Vitest 3.2+
- **Package Manager**: pnpm 10.24+
- **Node.js**: 18+

## 📄 License

ISC

---

**Created with** [start-ts-templates](https://github.com/royfw/start-ts-templates)