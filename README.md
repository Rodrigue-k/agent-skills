# 🧠 Agent Skills Repository

A curated, modular collection of **Production-Grade Engineering Skills & Standards** for AI coding assistants (Antigravity, Claude, Copilot, Gemini).

These skills transform AI assistants from general code generators into **Senior Principal Engineers and Product Architects** adhering to strict architectural patterns, zero-trust security, clean domain separation, UX ergonomics, and OS-native polish.

---

## 📦 Available Skills

### 📱 [`senior-mobile-developer`](./skills/senior-mobile-developer/SKILL.md)
Universal end-to-end senior engineering and product craft doctrine for production mobile applications:
- **Product Strategy & Page Rationalization**: The 4-Hat Mindset, "Page Justification" filter, streamlined navigation architecture (max 3-5 tabs, modal bottom sheets).
- **World-Class UI/UX Standards**: Strict zero-emoji policy, zero fake AI/marketing badges, non-flat refined gradients/surfaces, thumb-zone ergonomics (>= 48x48dp touch targets).
- **Native Bilingual i18n (FR/EN)**: Zero hardcoded user strings, strict dual-language parity from Day 0, resilience against text expansion.
- **Zero-Overflow Responsive Engine**: System `textScaler` clamping (0.85x - 1.15x), proportional ratio scaling context extensions, safe universal primitives (`AppButton`), keyboard avoidance scroll containers.
- **Domain-Driven Clean Architecture (DDD)**: Feature-First structure, 100% pure Dart `domain/` layer, reactive Inversion of Control ($UI = f(State)$), Zero-Trust client security with compile-time `--dart-define`.
- **4-State UI Contract & Error Architecture**: Canonical `Loading` (Shimmer/Skeleton), `Data/Success` (Pull-to-refresh), `Empty` (Illustration + CTA), and `Error` (Failure explanation + Retry button) states.
- **OS Polish & Diagnostics**: True Edge-to-Edge system bar overlays, native OS splash screens (`flutter_native_splash`), centralized declarative routing (`GoRouter`), and structured `AppLogger`.
- **Automated Verification Matrix**: Unit tests, state notifier/bloc tests, and widget contract tests (`mocktail`).

---

## 🚀 How to Use

### 1. Per-Project Installation
Copy any skill folder into your project’s `.agents/skills/` directory:
```bash
# Example: Add senior-mobile-developer to a mobile project
mkdir -p your-project/.agents/skills/senior-mobile-developer
cp -r path/to/agent-skills/skills/senior-mobile-developer/* your-project/.agents/skills/senior-mobile-developer/
```

### 2. Global Machine Installation (Antigravity)
Copy the skill to your global Antigravity config to make it available across all sessions:
```bash
# Windows (PowerShell)
mkdir -p "$HOME/.gemini/config/skills/senior-mobile-developer"
cp -r path/to/agent-skills/skills/senior-mobile-developer/* "$HOME/.gemini/config/skills/senior-mobile-developer/"

# macOS / Linux
mkdir -p ~/.gemini/config/skills/senior-mobile-developer
cp -r path/to/agent-skills/skills/senior-mobile-developer/* ~/.gemini/config/skills/senior-mobile-developer/
```

---

## 🛠️ Contributing New Skills

To add a new skill to this repository:
1. Create a directory under `skills/<skill-name>/`.
2. Add a `SKILL.md` with standard YAML frontmatter (`name`, `description`).
3. Ensure the skill is **universal and framework-agnostic** (focus on design principles, doctrines, product thinking, and patterns rather than project-specific credentials).
