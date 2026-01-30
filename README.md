# The PSF Organizers Kit

The Python Software Community and Conference Organizers Kit is a comprehensive resource developed by members of the Python Software Community to support individuals and groups in organizing Python-related events and fostering local communities. Adapted from materials by PyLadies Global, this kit offers practical guidance for both new and experienced organizers.

## Prerequisites

Before getting started, you'll need to install the following tools:

### Required

- **[uv](https://docs.astral.sh/uv/)** - Python package manager
  ```bash
  # macOS/Linux
  curl -LsSf https://astral.sh/uv/install.sh | sh

  # or with Homebrew
  brew install uv
  ```

### Optional

- **[just](https://github.com/casey/just)** - Command runner (provides convenient shortcuts)
  ```bash
  # macOS
  brew install just

  # Linux
  cargo install just
  # or see https://github.com/casey/just#installation for other options
  ```

- **[lychee](https://github.com/lycheeverse/lychee)** - Link checker (for validating links in documentation)
  ```bash
  # macOS
  brew install lychee

  # Linux
  cargo install lychee
  ```

## Quick Start

1. Clone the repository:
   ```bash
   git clone https://github.com/psf/organizer-toolkit.git
   cd organizer-toolkit
   ```

2. Install dependencies:
   ```bash
   just install
   # or without just:
   uv sync
   ```

3. Start the development server:
   ```bash
   just serve
   # or without just:
   uv run mkdocs serve
   ```

4. Open your browser to [http://127.0.0.1:8000](http://127.0.0.1:8000)

## Available Commands

Run `just` to see all available commands, or use the equivalent `uv` commands directly:

| Command | uv Equivalent | Description |
|---------|---------------|-------------|
| `just install` | `uv sync` | Install dependencies |
| `just serve` | `uv run mkdocs serve` | Start development server (port 8000) |
| `just serve-port PORT` | `uv run mkdocs serve --dev-addr=127.0.0.1:PORT` | Start dev server on specific port |
| `just build` | `uv run mkdocs build` | Build the documentation site |
| `just validate` | `uv run mkdocs build --strict` | Build with strict validation |
| `just link-check` | `lychee --cache --verbose .` | Check all links (requires lychee) |
| `just check` | — | Run all quality checks |
| `just deploy` | `uv run mkdocs gh-deploy --force` | Deploy to GitHub Pages |
| `just clean` | — | Clean generated files and cache |
| `just help` | — | Show detailed help message |

## Common Workflows

**Development:**
```bash
just install && just serve
# or without just:
uv sync && uv run mkdocs serve
```

**Pre-publish validation:**
```bash
just check
# or without just:
uv run mkdocs build && lychee --cache --verbose .
```

**Clean build:**
```bash
just clean && just build
# or without just:
rm -rf site/ && uv run mkdocs build
```

## Contributing

Contributions are welcome! Please feel free to submit issues and pull requests.

## License

This project is maintained by the Python Software Foundation.
