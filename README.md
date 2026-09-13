# 🧠 Agent Skills Repository

A curated, modular collection of **Production-Grade Engineering Skills & Standards** for AI coding assistants (Antigravity, Claude, Copilot, Gemini).

These skills transform AI assistants from general code generators into **Senior Principal Engineers and Product Architects** adhering to strict architectural patterns, zero-trust security, clean domain separation, UX ergonomics, comprehensive test suites, and OS-native polish.

---

## 📦 Available Skills

### 📱 [`senior-mobile-developer`](./skills/senior-mobile-developer/SKILL.md)
Universal end-to-end senior engineering and product craft doctrine for production mobile applications, featuring **Modular Project Profiling** and an **8-Tier Testing Matrix**:

- **Project Profiling Matrix**: Intelligent adaptation based on project mode (*Enterprise / FinTech / High-Scale*, *Focused MVP / Product Launch*, *Local-First Standalone*).
- **Product Strategy & Page Rationalization**: The 4-Hat Mindset, "Page Justification" filter, streamlined navigation architecture (max 3-5 tabs, modal bottom sheets).
- **World-Class UI/UX Standards**: Strict zero-emoji policy, zero fake AI/marketing badges, non-flat refined gradients/surfaces, thumb-zone ergonomics (>= 48x48dp touch targets).
- **Adaptive Centralized Text & i18n**: 
  - *Multi-language*: Strict dual-language parity (`AppLocalizations` FR/EN).
  - *Single-language*: Clean centralized constants (`AppStrings`), zero forced translation overhead, guaranteed UI expansion safety (`FittedBox`, `Wrap`).
- **Homothetic Zero-Overflow Responsive Engine**: System `textScaler` clamping (0.85x - 1.15x), Screen Ratio Engine (`rW`, `rH`, `rSize`, `rSp`, `rPad` clamped 0.68x-1.15x), dynamic title protection (`FittedBox` scaleDown), safe universal primitives (`AppButton`), keyboard avoidance scroll containers.
- **Granular Action Loading & Button State Isolation**: Elimination of amateur multi-button spinner flashing. Scoped action enums (`loadingAction`), targeted spinner rendering on the tapped button only, graceful non-spinning disabling of sibling actions, and per-item loading tracking in lists.
- **Scalable Clean Architecture (DDD)**: Feature-First structure, 100% pure Dart `domain/` layer, reactive Inversion of Control ($UI = f(State)$), pragmatic layering (no useless pass-through UseCases on simple CRUD), Zero-Trust client security with compile-time `--dart-define`.
- **4-State UI Contract & Error Architecture**: Canonical `Loading` (Shimmer/Skeleton), `Data/Success` (Pull-to-refresh), `Empty` (Illustration + CTA), and `Error` (Failure explanation + Retry button) states on async views.
- **Comprehensive 8-Tier Testing Matrix (World-Class Standards)**:
  1. *Tier 1 (Domain & Unit Tests)*: Pure business logic, validation rules, DTO serialization.
  2. *Tier 2 (State & Notifier Tests)*: State transitions, failure mappings, granular loading isolation verification.
  3. *Tier 3 (Widget Contracts & Goldens)*: 4-state contract UI renders, multi-screen simulation (320dp, 390dp, 448dp), and 1.4x text-scale overflow tests.
  4. *Tier 4 (End-to-End & Critical Flows)*: Integration flows, deep link routing, auth redirect guards (`Patrol`, `Maestro`, `integration_test`).
  5. *Tier 5 (Chaos, Offline & Network Resilience)*: Slow 3G timeouts, HTTP 401 token refresh/logout, HTTP 500 recovery, offline-first local sync.
  6. *Tier 6 (Performance & Memory Profiling)*: 60/120fps scrolling, resource disposal leak verification, APK/IPA size budgeting.
  7. *Tier 7 (Security SAST & Secret Audits)*: Binary secret leak scanning, Keychain/Keystore encrypted storage.
  8. *Tier 8 (Accessibility a11y)*: Screen reader semantics, touch targets >= 48dp, contrast >= 4.5:1.
- **App Lifecycle & Background Sync**: Handling `resumed` / `paused` lifecycle states, automatic network re-sync on reconnect (`connectivity_plus`).
- **Observability & CI/CD Gates**: Structured `AppLogger`, Crashlytics/Sentry telemetry with privacy-safe breadcrumbs, automated GitHub Actions / Fastlane build pipelines.
- **OS Polish & Navigation**: True Edge-to-Edge transparent system bars, native OS splash screens (`flutter_native_splash`), centralized declarative routing (`GoRouter`).

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
