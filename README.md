# 🧠 Agent Skills Repository

A curated, modular collection of **Production-Grade Engineering Skills & Standards** for AI coding assistants (Antigravity, Claude, Copilot, Gemini).

These skills transform AI assistants from general code generators into **Senior Principal Engineers** adhering to strict architectural patterns, zero-trust security, clean domain separation, and OS-native polish.

---

## 📦 Available Skills

### 🏛️ [`senior-flutter-architect`](./skills/senior-flutter-architect/SKILL.md)
Universal senior engineering doctrine for production Flutter mobile applications:
- **System UI & OS Polish**: Edge-to-Edge transparency, native OS splash screens (`flutter_native_splash`), adaptive insets.
- **Zero-Trust Security**: No hardcoded API/backend keys; compile-time `--dart-define` configuration.
- **Clean Architecture (DDD)**: Pure Dart `domain/` layer, separate `data/` and `presentation/`.
- **Inversion of Control**: Reactive state management (Riverpod/Bloc), zero `setState` for async network flows.
- **4-State UI Contract**: Strict handling of `Loading`, `Data`, `Empty`, and `Error` states with retry.
- **Structured Diagnostics**: Centralized `AppLogger` replacing raw `print()`.
- **Declarative Routing**: Centralized route hierarchy with auth redirect guards and deep linking.
- **Comprehensive Testing Matrix**: Unit, state notifier, and widget testing with `mocktail`.

---

## 🚀 How to Use

### 1. Per-Project Installation
Copy any skill folder into your project’s `.agents/skills/` directory:
```bash
# Example: Add senior-flutter-architect to a Flutter project
mkdir -p your-project/.agents/skills/senior-flutter-architect
cp -r path/to/agent-skills/skills/senior-flutter-architect/* your-project/.agents/skills/senior-flutter-architect/
```

### 2. Global Machine Installation (Antigravity)
Copy the skill to your global Antigravity config to make it available across all sessions:
```bash
# Windows
mkdir -p "$HOME/.gemini/config/skills/senior-flutter-architect"
cp -r path/to/agent-skills/skills/senior-flutter-architect/* "$HOME/.gemini/config/skills/senior-flutter-architect/"

# macOS / Linux
mkdir -p ~/.gemini/config/skills/senior-flutter-architect
cp -r path/to/agent-skills/skills/senior-flutter-architect/* ~/.gemini/config/skills/senior-flutter-architect/
```

---

## 🛠️ Contributing New Skills

To add a new skill to this repository:
1. Create a directory under `skills/<skill-name>/`.
2. Add a `SKILL.md` with standard YAML frontmatter (`name`, `description`).
3. Ensure the skill is **universal and framework-agnostic** (focus on design principles, doctrines, and patterns rather than project-specific credentials).
