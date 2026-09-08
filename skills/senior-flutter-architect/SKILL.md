---
name: senior-flutter-architect
description: >-
  Universal Senior Mobile Architecture & Engineering Standards for production-grade Flutter applications.
  Enforces Clean Architecture (Domain-Driven Design), Inversion of Control & State Management (Riverpod/Bloc),
  Edge-to-Edge OS polish, Native Splash protocols, Zero-Trust Client Security, Structured Diagnostics (AppLogger),
  Declarative Routing & Deep Linking, Exhaustive 4-State UI Contracts, and Test-Driven Quality.
  Apply across ANY Flutter mobile project to ensure architectural consistency, scalability, and senior-level craft.
---

# 🏛️ Universal Senior Flutter Architecture & Mobile Engineering Standard

This document establishes the **Universal Engineering Doctrine** for building, auditing, and scaling production-grade mobile applications with Flutter. It is framework-agnostic regarding specific third-party APIs, and defines the non-negotiable architectural principles that every senior mobile engineer must uphold.

---

## 1. 🌐 System UI & OS-Native Polish

Mobile apps must feel like first-class citizens of the host operating system (Android & iOS).

### 🔴 Anti-Patterns (Junior / Sub-standard)
- Hardcoded black or white bands behind the status bar or navigation bar.
- Putting a fake `Future.delayed(Duration(seconds: 3))` timer in Flutter code for a splash screen.
- Layout breaking or keyboard overlapping input fields because `viewInsets` or scroll containers were omitted.

### 🟢 Senior Architectural Doctrine
1. **True Edge-to-Edge & Dynamic Overlays**:
   - The status bar and navigation bar must always be transparent, allowing the design system to draw beneath system bars.
   - Configure overlay brightness adaptively based on theme brightness:
   ```dart
   SystemChrome.setEnabledSystemUIMode(SystemUiMode.edgeToEdge);
   SystemChrome.setSystemUIOverlayStyle(
     const SystemUiOverlayStyle(
       statusBarColor: Colors.transparent,
       statusBarIconBrightness: Brightness.dark, // or Brightness.light adaptively
       systemNavigationBarColor: Colors.transparent,
       systemNavigationBarIconBrightness: Brightness.dark,
     ),
   );
   ```
2. **Native OS Splash Protocol**:
   - The splash screen belongs to the native OS window manager (`launch_background.xml` / Android 12+ Splash API and iOS `LaunchScreen.storyboard`), configured via `flutter_native_splash`.
   - Once Flutter engine attaches to the window (`runApp`), render the initial destination immediately. Zero artificial delay timers.
3. **Responsive Window Insets & Keyboard Avoidance**:
   - Forms and interactive views must always be wrapped in a scrollable container (`SingleChildScrollView`, `ListView`, or `CustomScrollView`) with `keyboardDismissBehavior: ScrollViewKeyboardDismissBehavior.onDrag`.
   - Never use arbitrary fixed heights for modal sheets; constrain with `MediaQuery.viewInsetsOf(context)` and `MediaQuery.viewPaddingOf(context)`.

---

## 2. 🔒 Zero-Trust Client Security & Secrets Doctrine

### 🔴 Anti-Patterns
- Hardcoding sensitive backend credentials, master keys, service role keys, or admin API tokens directly in client Dart source code.
- Committing `.env` files with secret keys to version control.

### 🟢 Senior Architectural Doctrine
1. **The Client/Backend Security Boundary**:
   - **Rule**: If a key has administrative, write-all, or bypass permissions, it **MUST NEVER** exist inside a client application binary (APK/IPA). Client binaries can be decompiled in seconds.
   - Client applications only hold **Public / Publishable Identifiers** (e.g., Public Client IDs, Public API Keys).
   - Sensitive operations (database admin queries, password resets, payment captures) must always execute on a trusted backend or Edge function.
2. **Compile-Time Environment Injection**:
   - Inject environment-specific configuration at build time:
     `flutter build apk --dart-define=API_BASE_URL=https://api.example.com --dart-define=PUBLIC_KEY=pk_...`
   - Read safely in code:
     `static const String apiBaseUrl = String.fromEnvironment('API_BASE_URL', defaultValue: '...');`

---

## 3. 🧩 Domain-Driven Clean Architecture

Group code strictly by **Business Domain Features**, not by technical layers alone.

```
lib/
├── core/
│   ├── config/              # Environment configurations & compile-time variables
│   ├── di/                  # Dependency Injection container & root providers
│   ├── errors/              # Universal Failure & Exception models
│   ├── network/             # HTTP client interceptors, connectivity monitors
│   ├── theme/               # Semantic design tokens, typography, system UI styles
│   ├── utils/               # Structured AppLogger, formatters, extensions
│   └── widgets/             # Core reusable UI primitives (shimmers, buttons, dialogs)
└── features/
    └── [feature_name]/
        ├── data/
        │   ├── datasources/ # Remote API clients, local SQLite/Hive storage, WebSockets
        │   ├── dto/         # Data Transfer Objects (fromMap / toMap / fromJson / toJson)
        │   └── repositories/# Concrete repository implementations
        ├── domain/
        │   ├── entities/    # Pure Dart business objects (immutable, ZERO serialization logic)
        │   ├── repositories/# Abstract repository contracts (interface I[Feature]Repository)
        │   └── usecases/    # Single-responsibility business use cases (e.g. GetUserProfileUseCase)
        └── presentation/
            ├── providers/   # State holders (AsyncNotifiers, Blocs, Cubits, ViewModels)
            ├── screens/     # Top-level screen widgets (Pure UI renderers)
            └── widgets/     # Feature-specific sub-components
```

### 💎 Key Purity Rule:
- The `domain/` layer must be **100% pure Dart**. It must never import `dart:io`, `package:flutter`, or database libraries. It contains pure business entities and abstract interfaces.

---

## 4. ⚡ Inversion of Control & Reactive State Management

### 🔴 Anti-Patterns
- Calling `setState()` in widgets to perform async network or database operations inside `initState()`.
- Instantiating concrete services or repositories inside widgets (`final _repo = ConcreteRepository();`).
- Prop Drilling (passing mutable state down through many layers of widget constructors).

### 🟢 Senior Architectural Doctrine
1. **$UI = f(State)$**:
   - Widgets are pure renderers of state. They do not know *how* data is fetched, cached, or synchronized; they only receive immutable state snapshots.
2. **Inversion of Control (Dependency Injection)**:
   - Repositories and services are registered in the DI container (e.g. Riverpod Providers or GetIt) and injected into state controllers.
   ```dart
   // 1. Abstract Contract (Domain)
   abstract class IUserRepository {
     Future<UserEntity> getUser(String id);
   }

   // 2. Concrete Implementation (Data)
   class UserRepositoryImpl implements IUserRepository {
     final ApiClient _api;
     UserRepositoryImpl({required ApiClient api}) : _api = api;

     @override
     Future<UserEntity> getUser(String id) async { ... }
   }

   // 3. Dependency Injection
   final userRepositoryProvider = Provider<IUserRepository>((ref) {
     return UserRepositoryImpl(api: ref.watch(apiClientProvider));
   });
   ```
3. **Asynchronous State Producers**:
   - Use dedicated async state controllers (`AsyncNotifier`, `FutureProvider`, or `Bloc/Cubit`) that expose typed state with built-in reactivity and pull-to-refresh capabilities.

---

## 5. 🛡️ Exhaustive 4-State UI Contract & Error Architecture

### 🔴 Anti-Patterns
- Silently swallowing exceptions with empty catch blocks (`catch (_) {}`).
- Displaying raw technical stack traces (`Exception: SocketException 500`) directly to end users.
- Showing a blank screen when an error occurs or when a list is empty.

### 🟢 Senior Architectural Doctrine
1. **Universal Failure Hierarchy**:
   - Model all domain errors as typed immutable Failures:
   ```dart
   sealed class AppFailure {
     final String userMessage;
     const AppFailure(this.userMessage);
   }

   class NetworkFailure extends AppFailure {
     const NetworkFailure([super.userMessage = 'Vérifiez votre connexion internet.']);
   }

   class NotFoundFailure extends AppFailure {
     const NotFoundFailure([super.userMessage = 'La ressource demandée est introuvable.']);
   }

   class AuthFailure extends AppFailure {
     const AuthFailure([super.userMessage = 'Votre session a expiré. Veuillez vous reconnecter.']);
   }
   ```
2. **The 4 Canonical UI States**:
   Every data-driven view MUST explicitly render:
   - **`Loading`**: Shimmer or Skeleton matching the actual layout shape (never just a lone center spinner).
   - **`Data / Success`**: The rendered content with pull-to-refresh.
   - **`Empty`**: Meaningful illustration + explanation + primary Call to Action (e.g. "Créer", "Explorer").
   - **`Error`**: Human-readable explanation + Actionable **"Réessayer"** retry button.

---

## 6. 📊 Production Diagnostics & Structured Logging (`AppLogger`)

### 🔴 Anti-Patterns
- Calling `print()` or `debugPrint()` scattered across the codebase.
- Printing sensitive PII (passwords, tokens, phone numbers) to console.

### 🟢 Senior Architectural Doctrine
- All logs must flow through a centralized, structured `AppLogger`:
  - `AppLogger.d(msg)`: Verbose debug logs (automatically stripped in release).
  - `AppLogger.i(msg)`: High-level lifecycle & routing events.
  - `AppLogger.w(msg)`: Handled warnings / degraded states.
  - `AppLogger.e(msg, [error, stackTrace])`: Critical failures with structured stack traces.
- In Release builds, log levels are filtered and forwarded to observability backends (e.g. Sentry / Crashlytics).

---

## 7. 🧭 Declarative Routing & Deep Linking Standard

### 🔴 Anti-Patterns
- Uncontrolled `Navigator.push(context, MaterialPageRoute(...))` scattered in UI buttons.
- Broken deep links because routing is imperative and unmapped.

### 🟢 Senior Architectural Doctrine
1. **Centralized Route Hierarchy**:
   - Define a single declarative router (e.g. `GoRouter`) with structured route paths and nested shell routes for persistent bottom navigation.
2. **Route Guards**:
   - Handle authentication redirection centrally in the router `redirect` callback, not inside individual screen widgets.
3. **Universal Deep Linking**:
   - All shared entities must have path parameters (`/items/:id` or `/m/:id`) mapped to universal web links and native OS app links.

---

## 8. 🚀 Performance & Render Tree Hygiene

### 🟢 Senior Best Practices
- **`const` Constructors**: Mark every immutable widget with `const` to prune redundant widget rebuild subtrees.
- **RenderFlex Safety**:
  - Never put unbounded widgets inside horizontal `Row` or vertical `Column` without `Expanded`, `Flexible`, or `Wrap`.
  - Use `Wrap` for dynamic chips, tags, and badge rows where text length varies across locales.
- **Resource Lifecycle**: Always cancel Streams, Timers, AnimationControllers, and TextEditingControllers in `dispose()` or via Riverpod `ref.onDispose()`.

---

## 9. 🧪 Comprehensive Automated Testing Matrix

Senior code is verified by automated tests across three tiers:
1. **Unit Tests**: Pure business logic, Use Cases, DTO serialization, Model immutability.
2. **State & Provider Tests**: Verifying state transitions (Loading $\rightarrow$ Success, Loading $\rightarrow$ Error) using isolated DI containers.
3. **Widget & Interaction Tests**: Verifying UI contracts, tap triggers, empty state renders, and error retry flows using mocks (`mocktail`).
