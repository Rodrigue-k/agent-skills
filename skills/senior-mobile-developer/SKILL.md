---
name: senior-mobile-developer
description: >-
  Universal End-to-End Senior Mobile Engineering, Product & UI/UX Architecture Doctrine.
  Features Modular & Conditional Project Modes (Enterprise/Scale vs MVP/Monolingual vs Local-First).
  Enforces Product Discovery & Page Rationalization, World-Class UI/UX Standards (Zero-Emoji, Zero Fake-AI, Thumb-Zone ergonomics),
  Adaptive i18n & Centralized Text Architecture, Homothetic Zero-Overflow Responsive Engine (Screen Ratio Engine),
  Granular Button & Action Loading Isolation, Scalable Domain-Driven Clean Architecture (DDD), Exhaustive 4-State UI Contracts,
  End-to-End Testing Matrix (Unit, State, Golden/Visual, Integration/E2E, Chaos/Offline, Security & a11y),
  App Lifecycle & Background Sync, Edge-to-Edge OS Polish, Zero-Trust Client Security, and Observability/CI-CD.
  Apply across ANY mobile application project to build with senior-level craft and product thinking from day 0.
---

# 📱 Universal Senior Mobile Application Engineering & Product Doctrine

This doctrine establishes the **Complete Senior Lifecycle Framework** for conceiving, architecting, testing, and delivering world-class mobile applications. It empowers developers and AI agents to operate not merely as code generators, but as **Senior Product Engineers and Principal Mobile Architects** capable of tailoring standards intelligently to the specific scope, risk profile, and maturity of any project.

---

## 🎯 Modular Architecture & Project Profiling Matrix

Before writing code, the AI/engineer must identify the **Project Profile** to adapt requirements conditionally:

| Project Profile | Internationalization (i18n) | Architecture Depth | Testing Matrix Tier | Backend / Security | Observability & Release |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 🌐 **Enterprise / FinTech / High-Scale** | Strict Multi-language Parity (`AppLocalizations` FR/EN) | Full DDD Feature-First (Domain, Data, Presentation, UseCases) | Tiers 1 to 8 (Unit, State, Goldens, E2E, Chaos, a11y, Security) | Remote APIs, Zero-Trust secrets, compile-time `--dart-define` | Crashlytics/Sentry, Fastlane CI/CD, Feature Flags |
| ⚡ **Focused MVP / Product Launch** | Monolingual Centralized Strings (`AppStrings` / i18n ready) | Pragmatic Feature-First (Entities + Repositories + Notifiers) | Tiers 1, 2, 3 (Unit, State, Widget Contracts) | Targeted Backend / Firebase / Supabase | Structured `AppLogger`, basic error boundaries |
| 💾 **Local-First / Standalone Tool** | Single/Multi-language based on target audience | Domain-First with Local Storage DataSources (Isar, Hive, SQLite) | Tiers 1, 2, 5 (Unit, State, Offline/Sync & DB migrations) | Local encryption, zero remote secrets | Local structured logging, database backup |

---

## 🎭 The 4-Hat Mindset of the Senior Mobile Engineer

Before writing a single line of code, the engineer and AI must cycle through 4 distinct personas:

```mermaid
graph LR
    A["1. Product Strategist<br/>(Value, Scope & Page Rationalization)"] --> B["2. Principal UI/UX Designer<br/>(Design System & Ergonomics)"]
    B --> C["3. Senior Software Architect<br/>(Clean DDD, State & Granular Loading)"]
    C --> D["4. Production & QA Engineer<br/>(Testing Matrix, Polish & Insets)"]
```

1. **Product Strategist**: Profile project scope, challenge the need for every screen, eliminate friction, and streamline the core value loop.
2. **Principal UI/UX Designer**: Build cohesive design tokens, enforce thumb-friendly ergonomics, and reject amateur visuals.
3. **Senior Software Architect**: Enforce pure domain models, reactive state, typed failures, granular loading states, and conditional architecture depth.
4. **Production & QA Engineer**: Execute the comprehensive multi-tier testing matrix, ensure zero overflow, homothetic scaling, OS edge-to-edge transparency, and lifecycle resilience.

---

## 1. 🧭 Phase 1: Product Strategy & Page Rationalization

### 🔴 Anti-Patterns (Junior / Sub-standard)
- Creating a separate full-page screen for every tiny interaction or confirmation.
- Adding complex multi-step forms where a single focused sheet would suffice.
- Forcing users through bloated onboarding flows before demonstrating immediate core value.
- Cluttering the main navigation with 6+ bottom bar tabs.

### 🟢 Senior Architectural Doctrine

#### The "Page Justification" Filter:
For every screen requested or planned, ask:
1. **Core Purpose**: What single primary action or decision does the user make on this screen?
2. **Modal vs. Screen**: Can this be an interactive Bottom Sheet, an inline expandable card, or a confirmation snackbar rather than a heavy full route?
3. **Data Efficiency**: Does this screen require network roundtrips that could be prefetched or cached?
4. **Navigation Depth**: Keep critical user journeys under 3 taps from the home dashboard.

#### Core Navigation Architecture:
- **Bottom Navigation**: 3 to 5 tabs maximum (e.g., *Home/Explore, Search/Activity, Main Value Loop, Messages/Notifications, Profile/Settings*).
- **Secondary Flows**: Presented via adaptive Bottom Sheets (`showModalBottomSheet` with `isScrollControlled: true`) or dedicated nested routes.
- **Contextual Actions**: Place high-frequency actions within the primary thumb reach zone (bottom 40% of the viewport).

---

## 2. 🎨 Phase 2: World-Class UI/UX Design System & Visual Integrity

### 🔴 Anti-Patterns (Junior / Sub-standard)
- ❌ **Using Emojis in the UI**: Putting Unicode emojis in buttons, titles, badges, or headers.
- ❌ **Fake AI & Marketing Badges**: Slapping "99% AI Match" or fake compatibility meters not backed by real backend models.
- ❌ **Badge Overload**: Adding 4-5 repetitive tag chips to every list card, cluttering visual hierarchy.
- ❌ **Flat & Lifeless Surfaces**: Using flat, harsh monochrome backgrounds without subtle depth or contrast.
- ❌ **Tiny Touch Targets**: Buttons and icon buttons smaller than 44x44 dp.

### 🟢 Senior Architectural Doctrine

1. **Strict Zero-Emoji Policy**:
   - Use exclusively professional vector iconography (`LucideIcons`, `MaterialSymbols`, or custom SVGs).
   - Emojis cheapen institutional apps and render inconsistently across Android and iOS vendors.

2. **Visual Depth & Semantic Palette**:
   - Utilize refined gradients and surface layers for headers and action cards:
     - `headerGradientStart` -> `headerGradientEnd`
     - `surfaceLight` vs `surfaceDark` with subtle borders (`1px` with `0.08` opacity).
   - Maintain high contrast ratios (>= 4.5:1) for accessibility compliance (WCAG AA).

3. **Sobriety & Hierarchy**:
   - Max 1-2 contextual badges per card (e.g., *Status*, *Category*).
   - Clear typographical rhythm based on an 8pt grid system (8, 16, 24, 32 dp).

4. **Thumb-Zone Mobile Ergonomics**:
   - Primary Call to Action (CTA) must always be sticky at the bottom or reachable with one hand.
   - Minimum interactive touch target: 48x48 dp.

---

## 3. 🌍 Phase 3: Adaptive Internationalization (i18n) & Centralized Text Architecture

### 🔴 Anti-Patterns
- Hardcoding raw user-facing strings (`Text("Connexion")` or `Text("Submit")`) directly in widgets.
- Forcing full bilingual translation overhead on single-language local MVPs when not requested.
- Neglecting text expansion: designing fixed-width containers that break when translated to longer languages (French text is typically 20–30% longer than English).

### 🟢 Senior Architectural Doctrine (Conditional Implementation)

#### 🔀 Condition A: Multi-Language / International Project (e.g., French + English Parity)
- **Mandatory Dual-Dictionary**: Every string presented to the user (titles, labels, buttons, tooltips, validation errors, dialogs, empty states) MUST be registered in the localization dictionary (`AppLocalizations`).
- **Strict Parity**: Every key must have natural, verified translations in **both French (`fr`) and English (`en`)**.
- **Access Pattern**:
  ```dart
  Text(AppLocalizations.of(context).loginButtonLabel)
  ```

#### 🔀 Condition B: Single-Language Project / Local MVP (e.g., 100% French or 100% English)
- **Centralized Text Architecture**: Zero raw strings scattered in widget trees. All strings are organized in a dedicated semantic constants class (`AppStrings` or single-locale `AppLocalizations`).
- **Zero Translation Overhead**: Do NOT invent or force a secondary language file if the product specifications do not require it.
- **Future-Ready Contract**:
  ```dart
  // Clean centralized access
  Text(AppStrings.loginButtonLabel)
  ```

#### 📐 Universal Text Resilience (Applies to ALL Projects):
- Never set rigid fixed `width` on containers holding user text.
- Always protect text with `Wrap`, `Flexible`, `Expanded`, or `FittedBox(fit: BoxFit.scaleDown)` with `maxLines` and `TextOverflow.ellipsis`.

---

## 4. 📐 Phase 4: Homothetic Responsive Engine & Zero-Overflow Doctrine

### 🔴 Anti-Patterns
- Using hardcoded pixel dimensions (`width: 350`, `height: 80`) that break on small phones (SE 320-375dp) or stretch awkwardly on tablets.
- Unhandled system accessibility text zoom breaking UI buttons and header text.
- Yellow/Black `RenderFlex overflowed by X pixels` stripes when the on-screen keyboard appears.
- Header titles truncated with ellipsis (`...`) on compact devices due to fixed layout widths.

### 🟢 Senior Architectural Doctrine

1. **System Text-Scaling Bounds**:
   - Clamp the OS accessibility text scaler at the root widget to prevent destructive layout blowups:
   ```dart
   MaterialApp(
     builder: (context, child) {
       final mediaQuery = MediaQuery.of(context);
       return MediaQuery(
         data: mediaQuery.copyWith(
           textScaler: mediaQuery.textScaler.clamp(minScaleFactor: 0.85, maxScaleFactor: 1.15),
         ),
         child: child!,
       );
     },
   );
   ```

2. **Screen Ratio Engine (Homothetic Proportional Scaling)**:
   - Provide centralized, high-precision extensions calibrated on the reference canvas (`kRefScreenWidth = 390.0` or `448.0`, `kRefScreenHeight = 844.0` or `998.0`):
   ```dart
   extension ResponsiveExtensions on BuildContext {
     Size get screenSize => MediaQuery.sizeOf(this);
     double get screenWidth => screenSize.width;
     double get screenHeight => screenSize.height;

     bool get isMobile => screenWidth < 768;
     bool get isTablet => screenWidth >= 768 && screenWidth < 1024;
     bool get isDesktop => screenWidth >= 1024;

     // Ratio factors with broad adaptive bounds (0.68x - 1.15x) for compact devices
     double get widthRatio => isMobile ? (screenWidth / kRefScreenWidth).clamp(0.68, 1.15) : 1.0;
     double get heightRatio => isMobile ? (screenHeight / kRefScreenHeight).clamp(0.68, 1.15) : 1.0;

     /// Proportional width
     double rW(double size) => (size * widthRatio).roundToDouble();

     /// Proportional height
     double rH(double size) => (size * heightRatio).roundToDouble();

     /// Proportional square element (avatars, icons, action buttons, bell triggers)
     double rSize(double size) => (size * widthRatio).roundToDouble();

     /// Proportional fluid typography
     double rSp(double fontSize) => (fontSize * widthRatio).roundToDouble();

     /// Proportional padding and spacing
     double rPad(double space) => (space * widthRatio).roundToDouble();
   }
   ```

3. **Dynamic Title & Header Protection (`FittedBox`)**:
   - Wrap dynamic header titles, username greetings, and metrics in `FittedBox(fit: BoxFit.scaleDown)` with `maxLines: 1` to ensure zero truncated ellipses (`...`) on compact phones.

4. **Protected Universal Primitives (`AppButton`)**:
   - Buttons must encapsulate loading spinners, disabled states, and text protection:
   ```dart
   class AppButton extends StatelessWidget {
     final String text;
     final VoidCallback? onPressed;
     final bool isLoading;
     final bool isDisabled;
     
     const AppButton({
       super.key,
       required this.text,
       required this.onPressed,
       this.isLoading = false,
       this.isDisabled = false,
     });

     @override
     Widget build(BuildContext context) {
       final effectiveDisabled = isDisabled || isLoading || onPressed == null;
       return SizedBox(
         height: context.rW(52),
         width: double.infinity,
         child: ElevatedButton(
           onPressed: effectiveDisabled ? null : onPressed,
           child: isLoading
               ? SizedBox(
                   width: context.rW(22),
                   height: context.rW(22),
                   child: const CircularProgressIndicator(strokeWidth: 2.2),
                 )
               : FittedBox(
                   fit: BoxFit.scaleDown,
                   child: Text(text, maxLines: 1),
                 ),
         ),
       );
     }
   }
   ```

5. **Keyboard Avoidance & Scroll Hygiene**:
   - Interactive forms and input screens must always be wrapped in:
   ```dart
   SingleChildScrollView(
     keyboardDismissBehavior: ScrollViewKeyboardDismissBehavior.onDrag,
     padding: EdgeInsets.only(
       left: context.rPad(16),
       right: context.rPad(16),
       bottom: MediaQuery.viewInsetsOf(context).bottom + context.rPad(24),
     ),
     child: ...
   )
   ```

6. **Large Screen & Tablet Constraints**:
   - Cap maximum content width to `600dp` centered on tablet viewports:
   ```dart
   Center(
     child: ConstrainedBox(
       constraints: const BoxConstraints(maxWidth: 600),
       child: child,
     ),
   )
   ```

---

## 5. 🔘 Phase 5: Granular Button & Action Loading Isolation

### 🔴 Anti-Patterns (Amateur / "Violent" UI Loading)
- ❌ **Monolithic `isLoading` Flag**: Using a single global boolean `isLoading` on a screen containing multiple action buttons (e.g. "Continue with Google", "Continue with Apple", "Sign In with Email", or "Save Draft" vs "Publish").
- ❌ **Mass Button Spinning**: When the user taps one button, *every* button on the screen abruptly turns into a spinner simultaneously. This looks chaotic, amateurish, and confuses the user about which process is running.

### 🟢 Senior Architectural Doctrine (Conditional & Adaptive)

#### 🔀 Multi-Action Screens (Auth, Workflows, Wizard):
1. **Scoped Action Identifiers / Enums**:
   - Model asynchronous actions as typed enums or distinct identifiers:
   ```dart
   enum AuthAction { none, google, apple, emailPassword }

   class AuthState {
     final AuthAction loadingAction;
     final String? errorMessage;
     
     bool get isAnyLoading => loadingAction != AuthAction.none;
     bool isLoading(AuthAction action) => loadingAction == action;
   }
   ```

2. **Targeted Loader vs. Graceful Disabling**:
   - **Only the triggered button shows the spinner**: `isLoading: state.isLoading(AuthAction.google)`.
   - **Sibling buttons are safely disabled WITHOUT showing spinners**: `isDisabled: state.isAnyLoading`.
   ```dart
   // Google Button
   AppButton(
     text: strings.continueWithGoogle,
     isLoading: state.isLoading(AuthAction.google),
     isDisabled: state.isAnyLoading,
     onPressed: () => ref.read(authNotifierProvider.notifier).signInWithGoogle(),
   ),
   const SizedBox(height: 12),
   // Apple Button
   AppButton(
     text: strings.continueWithApple,
     isLoading: state.isLoading(AuthAction.apple),
     isDisabled: state.isAnyLoading,
     onPressed: () => ref.read(authNotifierProvider.notifier).signInWithApple(),
   ),
   ```

#### 🔀 Interactive Lists & Collections:
- In lists with row-level action triggers (e.g., "Follow", "Apply", "Delete", "Bookmark"), track loading state per item ID (`final Set<String> loadingItemIds;`).
- Only the row matching the tapped ID displays a spinner; the rest of the list remains clear and stable.

#### 🔀 Single-Action Dedicated Screens:
- On screens with a single isolated primary action (e.g., "Confirm SMS Code"), a simple boolean `isLoading` is fully acceptable and optimal.

---

## 6. 🏛️ Phase 6: Scalable Domain-Driven Clean Architecture

Adapt architecture depth to the project's scale:

```
lib/
├── core/
│   ├── config/              # Environment config & compile-time variables
│   ├── di/                  # Dependency Injection container & root providers
│   ├── errors/              # Universal Failure & Exception models
│   ├── localization/        # AppLocalizations (or AppStrings)
│   ├── network/             # HTTP client, interceptors (if remote backend)
│   ├── theme/               # Semantic design tokens, typography (AppTypography)
│   ├── utils/               # Structured AppLogger, formatters, extensions
│   └── widgets/             # Core reusable UI primitives (AppButton, AppTextField, Shimmer)
└── features/
    └── [feature_name]/
        ├── data/
        │   ├── datasources/ # Remote API / Local SQLite/Hive/Isar
        │   ├── dto/         # Data Transfer Objects (serialization)
        │   └── repositories/# Concrete repository implementations
        ├── domain/
        │   ├── entities/    # Pure Dart business objects (immutable, ZERO serialization)
        │   ├── repositories/# Abstract repository contracts (interface I[Feature]Repository)
        │   └── usecases/    # Business use cases (required for Enterprise, optional for simple CRUD)
        └── presentation/
            ├── providers/   # State controllers (AsyncNotifiers, Blocs, Cubits)
            ├── screens/     # Top-level screen widgets (Pure UI renderers)
            └── widgets/     # Feature-specific sub-components
```

### 💎 The Domain Purity Rule:
- The `domain/` layer must be **100% pure Dart**. It MUST NEVER import `package:flutter`, `dart:io`, or database drivers.

### ⚡ Pragmatic Clean Architecture vs Over-Engineering:
- **Enterprise / Scale**: Full layers with explicit UseCases for complex business orchestrations.
- **Focused MVP**: Pragmatic Clean Architecture (Entities + Abstract Repositories + Notifiers). Do NOT create pass-through UseCases that do nothing except forward a single call to the repository without business logic.

### 🔒 Zero-Trust Security (When Connecting to Remote Services):
- **Never store sensitive secrets in the app binary**: Admin keys, master database passwords, and service role keys must only live on the server or Edge functions.
- Inject public publishable variables at compile time:
  `flutter build apk --dart-define=API_BASE_URL=https://api.domain.com --dart-define=PUBLIC_KEY=pk_live_...`

---

## 7. 🛡️ Phase 7: Exhaustive 4-State UI Contract & Error Architecture

### 🔀 Asynchronous / Data-Driven Views:
Every screen that fetches data from an async source (Remote API, DB query, File I/O) MUST implement the **Canonical 4-State Contract**:

```mermaid
stateDiagram-v2
    [*] --> Loading: Fetch initiated
    Loading --> Success: Data received
    Loading --> Empty: Dataset is empty
    Loading --> Error: Exception occurred
    Error --> Loading: Tap 'Retry' button
    Success --> Loading: Pull-to-refresh
```

1. **Loading**: Content-shaped **Skeleton/Shimmer** loader matching the exact shape of the incoming content (never a solitary raw center spinner).
2. **Success / Data**: The rendered view with native **Pull-to-Refresh** (`RefreshIndicator`).
3. **Empty**: Contextual vector illustration + clear localized explanation + primary **Call to Action** button.
4. **Error**: Clear human-friendly explanation + prominent **"Réessayer / Retry"** action button.

### 🔀 Synchronous / Pure Form Screens:
- Do not invent artificial `Loading` or `Empty` states for instantaneous local views. Ensure instant rendering, responsive validation messages on fields, and clear snackbar/toast feedback on completion.

---

## 8. 🧪 Phase 8: Comprehensive 8-Tier Mobile Testing Matrix (World-Class Standards)

Senior mobile engineers and high-growth tech companies verify applications across an exhaustive **8-Tier Testing Matrix**. Apply each tier conditionally based on the project's risk and maturity profile:

```mermaid
graph TD
    T1["Tier 1: Pure Domain & Unit Tests"] --> T2["Tier 2: State Controller & Notifier Tests"]
    T2 --> T3["Tier 3: Widget Contracts & Golden Visual Tests"]
    T3 --> T4["Tier 4: End-to-End (E2E) & Integration Flows"]
    T4 --> T5["Tier 5: Chaos, Offline & Network Resilience Tests"]
    T5 --> T6["Tier 6: Performance, Frame Jank & Memory Leak Profiling"]
    T6 --> T7["Tier 7: Security SAST & Binary Secret Audits"]
    T7 --> T8["Tier 8: Accessibility (a11y) & Screen Reader Compliance"]
```

### 📋 Tier Breakdown & Execution Protocols:

#### 1. 🔬 Tier 1: Pure Domain & Unit Tests (Mandatory for ALL Projects)
- **Scope**: Entities, Value Objects, Business validation rules, DTO serialization/deserialization, Formatter utilities.
- **Rules**: Zero Flutter dependencies, executes in milliseconds, 100% deterministic (no real network or disk).
- **Example**:
  ```dart
  test('UserEntity calculates completion score accurately', () {
    final user = UserEntity(hasAvatar: true, hasResume: true, skillsCount: 4);
    expect(user.profileCompletionPercentage, 85);
  });
  ```

#### 2. ⚡ Tier 2: State Controller & Notifier Tests (Mandatory for ALL Projects)
- **Scope**: State transitions in Riverpod `AsyncNotifier`, Bloc `Cubit`, or ViewModel.
- **Verification**:
  - Initial $ightarrow$ Loading $ightarrow$ Success (with payload).
  - Initial $ightarrow$ Loading $ightarrow$ Failure (`AppFailure` mapped).
  - **Granular Loading Isolation**: Verify only the specific `loadingAction` changes during multi-button flows.
- **Tools**: `mocktail`, `flutter_test`.

#### 3. 🖼️ Tier 3: Widget Contracts & Golden Visual Tests
- **Scope**: Testing UI components across the 4 canonical states (*Loading Shimmer, Data, Empty, Error*).
- **Responsive Multi-Screen Simulation**: Testing widgets under simulated viewports:
  - Compact (320x568 - iPhone SE)
  - Standard (390x844 - iPhone 14/15)
  - Large (448x998 - Pixel 8 Pro / Pro Max)
- **Text-Scaling Tolerance**: Test widget under `textScaler: 1.4x` to guarantee zero `RenderFlex overflow`.
- **Golden Tests (Enterprise/Scale)**: Pixel-perfect snapshot regression tests verifying Light/Dark mode appearance.

#### 4. 🔄 Tier 4: End-to-End (E2E) & Critical Flow Tests
- **Scope**: Automated navigation through entire business user journeys (e.g., *Onboarding $ightarrow$ Sign In $ightarrow$ Search Job $ightarrow$ Submit Application $ightarrow$ Confirmation*).
- **Route & Guard Verification**: Verify unauthenticated users hitting `/profile` are redirected to `/login`, and deep links `/jobs/:id` navigate to the correct detail view.
- **Tools**: `integration_test`, `Patrol`, or `Maestro`.
- *Condition*: Required for Enterprise / Production apps; optional for early MVPs.

#### 5. 🔌 Tier 5: Chaos, Offline & Network Resilience Tests
- **Scope**: How the app survives real-world mobile conditions:
  - **Network Timeout & Slow 3G**: Ensuring timeouts throw user-friendly `NetworkFailure` with retry triggers.
  - **HTTP 401 Unauthorized**: Ensuring expired tokens trigger automatic silent refresh or clean logout.
  - **HTTP 500 Server Errors**: Ensuring graceful error states without crashing.
  - **Offline-First Mode**: Verifying cached data displays immediately when disconnected from internet.

#### 6. 🏎️ Tier 6: Performance, Frame Jank & Memory Leak Profiling
- **Target**: Continuous 60fps / 120fps scrolling with zero frame drops (render time $< 16\,	ext{ms}$ per frame).
- **Resource Disposal Verification**: Automated test verifying all `StreamSubscription`, `TextEditingController`, `AnimationController`, and `Timer` instances are cancelled when navigating away.
- **Binary Size Budget**: Monitoring APK/AAB and IPA binary size to prevent asset bloat.

#### 7. 🔒 Tier 7: Security SAST & Binary Secret Audits
- **Scope**:
  - Scanning compiled binaries to ensure **zero private API keys, master passwords, or tokens** are embedded in plaintext.
  - Verifying sensitive data stored locally uses encrypted containers (`FlutterSecureStorage` with Android KeyStore / iOS Keychain).
  - Verifying SSL Pinning and Certificate Transparency for FinTech/Banking apps.

#### 8. ♿ Tier 8: Accessibility (a11y) & Screen Reader Compliance
- **Scope**:
  - Verify every interactive button has a clear semantic label for TalkBack / VoiceOver.
  - Minimum touch target verification ($\ge 48 	imes 48\,	ext{dp}$).
  - Contrast ratio verification ($\ge 4.5:1$ for normal text, $\ge 3.0:1$ for large headings).

---

## 9. 🔄 Phase 9: App Lifecycle, Background Sync & Observability

Enterprise-grade mobile apps handle OS interruptions gracefully:

1. **App Lifecycle Management (`WidgetsBindingObserver`)**:
   - **`AppLifecycleState.resumed`**: Refresh stale auth tokens, check for critical remote config updates, resume paused UI timers.
   - **`AppLifecycleState.paused` / `inactive`**: Pause resource-heavy streams, camera controllers, and sensor polling to preserve battery.

2. **Network Reconnection Synchronization**:
   - Monitor connection state (`connectivity_plus`). Automatically re-sync pending offline actions (e.g. queued form submissions) when internet returns.

3. **Structured Diagnostics & Crash Telemetry**:
   - Strictly prohibit raw `print()` statements.
   - Centralized `AppLogger` (`d`, `i`, `w`, `e`) integrated with Sentry or Firebase Crashlytics:
     - Automatically attach non-sensitive breadcrumbs (user navigation path) to crash reports.
     - **Strict Privacy Rule**: Never send PII, passwords, or credit card numbers to external logging servers.

4. **CI/CD Automated Release Gates (Fastlane / GitHub Actions)**:
   - Automated pipeline triggering on pull requests:
     1. `flutter analyze` (Zero warnings/lint errors).
     2. `flutter test` (Unit, State, Widget contracts).
     3. Automated build of release AAB/IPA with `--dart-define` compilation.

---

## 10. 🚀 Phase 10: OS-Native Polish, Routing & Production Deployment

1. **True Edge-to-Edge System Bars**:
   - Transparent navigation and status bars with adaptive icon brightness:
   ```dart
   SystemChrome.setEnabledSystemUIMode(SystemUiMode.edgeToEdge);
   SystemChrome.setSystemUIOverlayStyle(
     const SystemUiOverlayStyle(
       statusBarColor: Colors.transparent,
       statusBarIconBrightness: Brightness.dark,
       systemNavigationBarColor: Colors.transparent,
       systemNavigationBarIconBrightness: Brightness.dark,
     ),
   );
   ```

2. **Native OS Splash Screen Protocol**:
   - Splash screens belong to the native OS window manager (`flutter_native_splash` configuring Android 12+ Splash API and iOS `LaunchScreen.storyboard`).
   - Zero artificial `Future.delayed(Duration(seconds: 3))` timers in Flutter code.

3. **Declarative Routing & Deep Linking**:
   - Centralized declarative router (`GoRouter`) with authentication guards (`redirect` callback) and parameterized deep link routes (`/items/:id`).

---

## 🤖 Step-by-Step AI Execution Protocol

When prompted to create or evolve a mobile feature, the AI MUST follow this exact sequence:

1. **Step 1 (Project Profiling & Product Scope)**:
   - Identify project mode: Enterprise/Bilingual vs MVP/Monolingual vs Local-First.
   - Challenge screen count. Propose the minimal, most intuitive flow.
2. **Step 2 (Design System & Centralized Text)**:
   - Determine text strategy (`AppLocalizations` FR/EN or `AppStrings`).
   - Confirm typography tokens, non-flat surface gradients, and vector iconography.
3. **Step 3 (Domain & Contracts)**:
   - Write pure Dart entities and abstract repository contracts.
4. **Step 4 (Data, State & Granular Loading)**:
   - Implement data sources, DTOs, and reactive state notifiers with typed failures and isolated action loading identifiers (`loadingAction`).
5. **Step 5 (Presentation with UI Contracts & Homothetic Responsiveness)**:
   - Build UI using `AppButton`, `context.rW()`, `context.rH()`, `context.rSize()`, `context.rSp()`, `FittedBox` title safety, keyboard scroll hygiene, and shimmer loading.
6. **Step 6 (Testing & QA Execution)**:
   - Write Unit tests (Domain & DTOs), State Notifier tests, and Widget contract tests (testing 320dp, 390dp, 448dp + 1.4x text scaling).
7. **Step 7 (OS Polish & Verification)**:
   - Verify Edge-to-Edge compliance, zero hardcoded strings, zero emojis, zero shared loading flashes, lifecycle cleanup, and run automated test suite.
