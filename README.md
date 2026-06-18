# Nitpick Programming Language

<p align="center">
    <img src="assets/nitpick_logo.png" alt="Nitpick logo: raccoon holding a magnifying glass" width="240">
</p>


**A safety-critical programming language for deterministic systems.**

Nitpick is a compiled language with an LLVM backend, designed for systems where correctness, determinism, and safety are paramount. It features a strong type system, atomic operations, trit/nit logic, and a growing ecosystem of packages and tools.

## Repositories

The Nitpick project is organized across multiple repositories under the [Alternative Intelligence](https://github.com/alternative-intelligence-cp) organization.

### Core

| Repository | Description |
|-----------|-------------|
| [nitpick](https://github.com/alternative-intelligence-cp/nitpick) | **Compiler, stdlib, runtime, LSP, debugger, package manager** — the core language implementation |
| [nitpick-lang](https://github.com/alternative-intelligence-cp/nitpick-lang) | This repo — project hub and cross-repo coordination |
| [Web Documentation](https://ai-liberation-platform.org/nitpick/docs/) | **Official Web Docs** — easily navigable documentation, guides, and reference |

### Ecosystem

| Repository | Description |
|-----------|-------------|
| [nitpick-packages](https://github.com/alternative-intelligence-cp/nitpick-packages) | 113 ecosystem packages (networking, GUI, audio, testing, etc.) |
| [nitpick-build](https://github.com/alternative-intelligence-cp/nitpick-build) | Build system with ABC config format and FFI support |
| [nitpick-docs](https://github.com/alternative-intelligence-cp/nitpick-docs) | Documentation, man pages, examples, and language specs |
| [nitpick-tools](https://github.com/alternative-intelligence-cp/nitpick-tools) | Developer tools — safety audit, MCP server, editor support, VS Code extension |
| [nitpick-specialist](https://github.com/alternative-intelligence-cp/nitpick-specialist) | AI specialist model training infrastructure (Qwen-based fine-tunes) |
| [nitpick-packages-apt](https://github.com/alternative-intelligence-cp/nitpick-packages-apt) | APT repository infrastructure for Debian/Ubuntu packages |
| [nitpick-posix](https://github.com/alternative-intelligence-cp/nitpick-posix) | POSIX compatibility and utilities |
| [nitpick-ports](https://github.com/alternative-intelligence-cp/nitpick-ports) | Software ports to the Nitpick ecosystem |

### Applications

| Repository | Description |
|-----------|-------------|
| [nitty](https://github.com/alternative-intelligence-cp/nitty) | Advanced terminal emulator |
| [neditor](https://github.com/alternative-intelligence-cp/neditor) | High-performance GUI code editor |
| [nalculator](https://github.com/alternative-intelligence-cp/nalculator) | Precision calculator application |
| [napit](https://github.com/alternative-intelligence-cp/napit) | Cross-platform API client |
| [nitpick-studio](https://github.com/alternative-intelligence-cp/nitpick-packages/tree/main/packages/nitpick-debugger) | Official graphical debugger IDE |

### Distribution

| Repository | Description |
|-----------|-------------|
| [nitpicker](https://github.com/alternative-intelligence-cp/nitpicker) | NitpickX Linux distribution — custom kernel, shell, and desktop environment |

### Community

| Repository | Description |
|-----------|-------------|
| [nitpick-community](https://github.com/alternative-intelligence-cp/nitpick-community) | GitHub Discussions, governance, RFCs, and community showcase |

---

## Quick Start

### Install from APT (Ubuntu 24.04 / Linux Mint 22.x)
```bash
curl -fsSL https://packages.npker.ai-liberation-platform.org/setup-repo.sh | sudo bash
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
nitpick (compiler)
├── npkc           — Compiler (Nitpick → LLVM IR → native)
├── nitpick-ls        — Language Server Protocol implementation
├── npkpkg         — Package manager
├── nitpick-doc       — Documentation generator
├── stdlib/        — Standard library (ships with compiler)
└── tests/         — Compiler + stdlib test suite

nitpick-packages   — 113 ecosystem packages
nitpick-build      — Build system, npkbld
nitpick-docs       — Docs, man pages, 78+ examples
nitpick-tools      — Safety audit, MCP, editors, VS Code
nitpick-specialist — AI model training (Qwen2.5-7B fine-tune)
nitpick-packages-apt — APT repo infrastructure
nitpicker          — Nitpicker Linux distribution
```

## Organization

All repositories are maintained under the [**Alternative Intelligence**](https://github.com/alternative-intelligence-cp) organization.

### Nitpick Umbrella
The Nitpick project and everything built around it — compiler, packages, tools, the NitpickX distribution.

| Project | Description |
|---------|-------------|
| **Nitpick** | Safety-critical programming language (this project) |
| [nitpicker](https://github.com/alternative-intelligence-cp/nitpicker) | NitpickX Linux distribution |

### Related Projects

| Project | Description |
|---------|-------------|
| [Nikola](https://github.com/alternative-intelligence-cp/nikola) | AI/ML platform — the reason Nitpick exists, but its own project |
| [nikos](https://github.com/alternative-intelligence-cp/nikos) | NIKOS — IKOS static analyzer updated to LLVM 20 for Nikola development |
| [Educational](https://github.com/alternative-intelligence-cp/educational) | Deep-dive educational material — not "here's how to use the thing," but *how the thing works and why* |
| [Tech](https://github.com/alternative-intelligence-cp/tech) | Things we built for fun or because we needed them |
| [Website](https://github.com/alternative-intelligence-cp/ailp-website) | Organization website (ai-liberation-platform.org) |

## Current Release

**v0.60.4.1** (Stable)
- LLVM 20.1.2 backend
- 113 ecosystem packages
- Full module system (`use`, `mod`, `pub`, cross-module visibility)
- GTK4, SDL2, Raylib GUI wrappers
- LSP with document symbols, references, signature help
- DAP debugger with conditional breakpoints
- MCP server for AI-assisted development
- nitpick-safety static analysis tool
- Debian package (.deb)

## License

AGPL-3.0 — see [LICENSE.md](LICENSE.md) in each repository.
