# bin-tsdown - Documentation

## 📑 Table of Contents

- [Project Overview](#-project-overview)
- [Quick Start](#-quick-start)
- [CLI Usage](#-cli-usage)
- [Core Features](#-core-features)
- [Project Structure](#-project-structure)
- [Development](#-development)
- [Building CLIs](#-building-clis)
- [Testing](#-testing)
- [Publishing](#-publishing)
- [Best Practices](#-best-practices)

## 🎯 Project Overview

**bin-tsdown** is a production-ready CLI tool template built with TypeScript and modern tooling. It combines Commander.js for command handling and Inquirer for interactive prompts, providing a solid foundation for building powerful command-line applications.

### Why bin-tsdown?

- **Interactive** - Rich prompts with Inquirer
- **Type Safe** - Full TypeScript support
- **Fast Builds** - tsdown for quick compilation
- **User Friendly** - Intuitive command structure
- **Production Ready** - Built-in error handling and validation

### Use Cases

- Project scaffolding tools
- File generators
- Build automation tools
- DevOps utilities
- Configuration management CLIs

## 🚀 Quick Start

### Prerequisites

- Node.js 18+
- pnpm 10.24+

### Installation

```bash
# Create from template
degit royfw/start-ts-templates/templates/bin-tsdown my-cli
cd my-cli

# Install dependencies
pnpm install

# Run in development
pnpm tsx
```

### First Run

```bash
# Run the CLI
pnpm tsx create my-project

# With template option
pnpm tsx create my-project -t user/repo

# Interactive mode (no arguments)
pnpm tsx create
```

## 🎯 CLI Usage

### Basic Commands

```bash
# Create command with name
your-cli create <project-name>

# Create with template option
your-cli create <project-name> -t <template>

# Interactive mode
your-cli create
```

### Command Options

```bash
-t, --template <repo>    GitHub template (e.g., user/repo)
-h, --help               Display help information
```

### Examples

```bash
# Create project interactively
your-cli create

# Create with all options
your-cli create my-app -t username/template-repo

# Get help
your-cli --help
```

## ✨ Core Features

### 1. Commander.js Integration

Powerful command-line interface framework:

- **Command Definition** - Clear command structure
- **Option Parsing** - Automatic argument handling
- **Help Generation** - Auto-generated help text
- **Subcommands** - Support for nested commands
- **Version Management** - Built-in version display

### 2. Inquirer Prompts

Interactive user input:

- **Multiple Input Types** - Text, list, confirm, etc.
- **Validation** - Built-in and custom validators
- **Conditional Prompts** - Dynamic question flow
- **Default Values** - Sensible defaults
- **Error Handling** - Graceful user interruption

### 3. Project Scaffolding

Template-based project creation:

- **GitHub Integration** - Clone from GitHub repos
- **Multiple Templates** - Support various project types
- **File Copying** - Automatic file distribution
- **Configuration** - JSON-based template config

### 4. Type Safety

Full TypeScript support:

- **Type Definitions** - Complete type coverage
- **IntelliSense** - IDE autocomplete support
- **Compile-Time Checks** - Catch errors early
- **Refactoring Safety** - Confident code changes

## 📁 Project Structure

```
bin-tsdown/
├── src/
│   ├── index.ts                    # CLI entry point
│   └── libs/
│       ├── index.ts               # Library exports
│       └── create.ts              # Create command logic
├── scripts/
│   ├── copyPackageJsonPlugin.ts   # Build plugin
│   └── copyFilesPlugin.ts         # File copy plugin
├── dist/
│   └── bin/
│       └── index.js               # Compiled CLI
├── templates.json                  # Template definitions
├── copyFiles.json                  # Files to copy
└── tsdown.config.ts               # Build configuration
```

## 🛠️ Development

### Available Scripts

```bash
# Development
pnpm dev                # Watch mode with type checking
pnpm tsx                # Run with tsx (instant start)

# Build
pnpm build              # Production build
pnpm clean              # Clean build artifacts

# Testing
pnpm test               # Run tests
pnpm vitest             # Interactive test mode
pnpm vitest:ui          # Test UI
pnpm vitest:e2e         # E2E tests

# Code Quality
pnpm lint               # Lint code
pnpm lint:fix           # Fix linting issues
pnpm typecheck          # Type checking
```

### Adding New Commands

1. **Define command in index.ts**:

```typescript
// src/index.ts
program
  .command('init [name]')
  .description('Initialize a new project')
  .option('-f, --force', 'Force overwrite')
  .action(async (name, options) => {
    await initProject({ name, force: options.force });
  });
```

2. **Implement command logic**:

```typescript
// src/libs/init.ts
export async function initProject(options: {
  name?: string;
  force?: boolean;
}) {
  // Implementation
}
```

3. **Add interactive prompts**:

```typescript
import inquirer from 'inquirer';

const answers = await inquirer.prompt([
  {
    type: 'input',
    name: 'name',
    message: 'Project name:',
    default: 'my-project'
  },
  {
    type: 'confirm',
    name: 'force',
    message: 'Overwrite existing files?',
    default: false
  }
]);
```

## 🎨 Building CLIs

### Command Structure

```typescript
// Basic command
program
  .command('create <name>')
  .description('Create a new project')
  .action((name) => {
    console.log(`Creating ${name}`);
  });

// Command with options
program
  .command('build')
  .option('-w, --watch', 'Watch mode')
  .option('-m, --minify', 'Minify output')
  .action((options) => {
    console.log('Building...', options);
  });
```

### Interactive Prompts

```typescript
// Text input
const { name } = await inquirer.prompt([
  {
    type: 'input',
    name: 'name',
    message: 'Enter your name:'
  }
]);

// List selection
const { framework } = await inquirer.prompt([
  {
    type: 'list',
    name: 'framework',
    message: 'Choose a framework:',
    choices: ['React', 'Vue', 'Angular']
  }
]);

// Confirmation
const { confirmed } = await inquirer.prompt([
  {
    type: 'confirm',
    name: 'confirmed',
    message: 'Are you sure?',
    default: false
  }
]);
```

### Error Handling

```typescript
try {
  await createProject({ name, template });
} catch (error) {
  if (error.name === 'ExitPromptError') {
    console.log('👋 Operation cancelled');
    process.exit(0);
  } else {
    console.error('❌ Error:', error);
    process.exit(1);
  }
}
```

### Template Configuration

```json
// templates.json
[
  {
    "name": "React App",
    "repo": "username/react-template"
  },
  {
    "name": "Node.js API",
    "repo": "username/node-template"
  }
]
```

## 🧪 Testing

### Unit Tests

```typescript
// src/libs/create.spec.ts
import { describe, it, expect } from 'vitest';
import { createProject } from './create';

describe('createProject', () => {
  it('should create project directory', async () => {
    await createProject({
      name: 'test-project',
      template: 'user/template'
    });
    // Assertions
  });
});
```

### E2E Tests

```typescript
// test/cli.e2e-spec.ts
import { describe, it, expect } from 'vitest';
import { exec } from 'child_process';
import { promisify } from 'util';

const execAsync = promisify(exec);

describe('CLI E2E', () => {
  it('should show help message', async () => {
    const { stdout } = await execAsync('node dist/bin/index.js --help');
    expect(stdout).toContain('Usage:');
  });
});
```

## 📦 Publishing

### Prepare for Publishing

1. **Update package.json**:

```json
{
  "name": "@yourscope/cli-name",
  "version": "1.0.0",
  "description": "Your CLI description",
  "bin": {
    "your-cli": "./dist/bin/index.js"
  },
  "files": [
    "dist",
    "templates.json"
  ],
  "keywords": ["cli", "tool", "typescript"]
}
```

2. **Add shebang to built file**:

```typescript
// Ensure index.ts starts with:
#!/usr/bin/env node
```

3. **Build and test**:

```bash
pnpm build
pnpm test

# Test locally
npm link
your-cli --help
```

### NPM Publishing

```bash
# Login to npm
npm login

# Publish
npm publish --access public

# Test installation
npx @yourscope/cli-name --help
```

### Global Installation

Users can install globally:

```bash
# Install globally
npm install -g @yourscope/cli-name

# Use anywhere
your-cli create my-project
```

## 🎯 Best Practices

### 1. User Experience

```typescript
// ✅ Good - Clear messages
console.log('✅ Project created successfully!');
console.log('📦 Installing dependencies...');

// ❌ Avoid - Unclear output
console.log('Done');
```

### 2. Error Handling

```typescript
// ✅ Good - Helpful error messages
if (!projectName) {
  console.error('❌ Error: Project name is required');
  console.log('💡 Try: your-cli create my-project');
  process.exit(1);
}

// ❌ Avoid - Generic errors
if (!projectName) {
  throw new Error('Invalid input');
}
```

### 3. Validation

```typescript
// ✅ Good - Validate early
const answers = await inquirer.prompt([
  {
    type: 'input',
    name: 'name',
    message: 'Project name:',
    validate: (input) => {
      if (!/^[a-z0-9-]+$/.test(input)) {
        return 'Name must contain only lowercase letters, numbers, and hyphens';
      }
      return true;
    }
  }
]);
```

### 4. Help Text

```typescript
// ✅ Good - Descriptive help
program
  .command('create <name>')
  .description('Create a new project from a template')
  .option('-t, --template <repo>', 'GitHub template repository (e.g., user/repo)')
  .action(handler);
```

## 📊 Performance Tips

- Use lazy loading for heavy dependencies
- Cache frequently accessed data
- Minimize file I/O operations
- Use streams for large files
- Provide progress indicators

## 🔒 Security

- Validate all user inputs
- Sanitize file paths
- Use secure dependencies
- Avoid executing arbitrary code
- Keep dependencies updated

## 🤝 Contributing

Contributions welcome! Please:
- Add tests for new commands
- Follow existing code style
- Update documentation
- Test CLI locally

## 📄 License

ISC

---

**Created with** [start-ts-templates](https://github.com/royfw/start-ts-templates)