# Aria Programming Language

<p align="center">
    <img src="assets/nitpick_logo.png" alt="Nitpick logo: raccoon holding a magnifying glass" width="240">
</p>

> 🚧 **Rebrand in progress:** Aria is becoming **Nitpick**. This hub repo still
> uses Aria names while the migration is underway. Existing repository history
> and links are being preserved; repo renames should prefer GitHub's in-place
> rename flow so redirects keep working.

**A safety-critical programming language for deterministic systems.**

Aria is a compiled language with an LLVM backend, designed for systems where correctness, determinism, and safety are paramount. It features a strong type system, atomic operations, trit/nit logic, and a growing ecosystem of packages and tools.

## Repositories

The Aria project is organized across multiple repositories under the [Alternative Intelligence](https://github.com/alternative-intelligence-cp) organization.

### Core

| Repository | Description |
|-----------|-------------|
| [aria](https://github.com/alternative-intelligence-cp/aria) | **Compiler, stdlib, runtime, LSP, debugger, package manager** — the core language implementation |
| [aria-lang](https://github.com/alternative-intelligence-cp/aria-lang) | This repo — project hub and cross-repo coordination |

### Ecosystem

| Repository | Description |
|-----------|-------------|
| [aria-packages](https://github.com/alternative-intelligence-cp/aria-packages) | 39 ecosystem packages (networking, GUI, audio, testing, etc.) |
| [aria-make](https://github.com/alternative-intelligence-cp/aria-make) | Build system with ABC config format and FFI support |
| [aria-docs](https://github.com/alternative-intelligence-cp/aria-docs) | Documentation, man pages, examples, and language specs |
| [aria-tools](https://github.com/alternative-intelligence-cp/aria-tools) | Developer tools — safety audit, MCP server, editor support, VS Code extension |
| [aria-specialist](https://github.com/alternative-intelligence-cp/aria-specialist) | AI specialist model training infrastructure (Qwen-based fine-tunes) |
| [aria-packages-apt](https://github.com/alternative-intelligence-cp/aria-packages-apt) | APT repository infrastructure for Debian/Ubuntu packages |

### Distribution

| Repository | Description |
|-----------|-------------|
| [ariax](https://github.com/alternative-intelligence-cp/ariax) | AriaX Linux distribution — custom kernel, shell, and desktop environment |

### Community

| Repository | Description |
|-----------|-------------|
| [aria_community](https://github.com/alternative-intelligence-cp/aria_community) | GitHub Discussions, governance, RFCs, and community showcase |

---

## Quick Start

### Install from APT (Ubuntu 24.04 / Linux Mint 22.x)
```bash
curl -fsSL https://packages.ariax.ai-liberation-platform.org/setup-repo.sh | sudo bash
sudo apt install nitpick
```

### Build from Source
```bash
git clone https://github.com/alternative-intelligence-cp/nitpick.git
cd nitpick
mkdir build && cd build
cmake .. -DCMAKE_BUILD_TYPE=Release
make -j$(nproc)
sudo make install
```

### Hello World
```nitpick
func:main = int32() {
    drop(println("Hello from Nitpick!"));
    exit(0);
};
func:failsafe = int32(tbb32:err) { exit(1); };
```
```bash
npkc hello.npk -o hello
./hello
```

## Architecture

```
aria (compiler)
├── npkc           — Compiler (Nitpick → LLVM IR → native, was ariac)
├── aria-ls        — Language Server Protocol implementation
├── npkpkg         — Package manager (was aria-pkg)
├── aria-doc       — Documentation generator
├── stdlib/        — Standard library (ships with compiler)
└── tests/         — Compiler + stdlib test suite

nitpick-packages   — 103 ecosystem packages
nitpick-build      — Build system, npkbld (was aria-make)
nitpick-docs       — Docs, man pages, 78+ examples
nitpick-tools      — Safety audit, MCP, editors, VS Code
nitpick-specialist — AI model training (Qwen2.5-7B fine-tune)
nitpick-packages-apt — APT repo infrastructure
nitpicker          — Nitpicker Linux distribution (was AriaX)
```

## Organization

All repositories are maintained under the [**Alternative Intelligence**](https://github.com/alternative-intelligence-cp) organization.

### Aria Umbrella
The Aria project and everything built around it — compiler, packages, tools, the AriaX distribution.

| Project | Description |
|---------|-------------|
| **Aria** | Safety-critical programming language (this project) |
| [ariax](https://github.com/alternative-intelligence-cp/ariax) | AriaX Linux distribution |

### Related Projects

| Project | Description |
|---------|-------------|
| [Nikola](https://github.com/alternative-intelligence-cp/nikola) | AI/ML platform — the reason Aria exists, but its own project |
| [Educational](https://github.com/alternative-intelligence-cp/educational) | Deep-dive educational material — not "here's how to use the thing," but *how the thing works and why* |
| [Tech](https://github.com/alternative-intelligence-cp/tech) | Things we built for fun or because we needed them |
| [Website](https://github.com/alternative-intelligence-cp/ailp-website) | Organization website (ai-liberation-platform.org) |

## Current Release

**v0.2.2** (in development)
- LLVM 20.1.2 backend
- 39 ecosystem packages
- GTK4, SDL2, Raylib GUI wrappers
- LSP with document symbols, references, signature help
- DAP debugger with conditional breakpoints
- MCP server for AI-assisted development
- aria-safety static analysis tool
- Debian package (.deb)

## License

AGPL-3.0 — see [LICENSE.md](LICENSE.md) in each repository.
