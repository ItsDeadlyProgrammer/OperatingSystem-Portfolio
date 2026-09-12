# Platform Support & Deployment

The OS Simulator is designed to be truly multi-platform. Below are the verified targets and their specific implementation details.

## Target Matrix

| Target | Architecture | UI Framework | Entry Point |
|---|---|---|---|
| **Android** | ARM64 / x86_64 | Compose | `MainActivity` |
| **Desktop** | JVM (Windows/Mac/Linux) | Compose | `Main.kt` |
| **Web** | WebAssembly (Wasm) | Compose | `index.html` |
| **iOS** | Native (ARM64) | Compose | `MainViewController` |

---

## 🤖 Android
The Android application provides a full-featured mobile experience.
- **Min SDK**: 24
- **Target SDK**: 34
- **Build Command**: `./gradlew :composeApp:assembleDebug`

## 💻 Desktop (JVM)
The desktop version is the primary environment for detailed analysis, offering the best performance for complex graph visualizations.
- **Runtime**: JDK 17+ (JDK 21 recommended for build)
- **Run Command**: `./gradlew :composeApp:run`
- **Distribution**: MSI (Windows), DMG (macOS), DEB (Linux)

## 🌐 Web (WasmJs)
The web version allows users to try the simulator without installation. It uses the latest Kotlin/Wasm technology.
- **Technology**: WasmJs
- **Development Command**: `./gradlew :composeApp:wasmJsBrowserDevelopmentRun`
- **Production Command**: `./gradlew :composeApp:wasmJsBrowserDistribution`
- **Default URL**: `http://localhost:8080/`

## 🍏 iOS
The project includes the infrastructure for iOS support via Compose Multiplatform.
- **Status**: Infrastructure present and configured in `build.gradle.kts`.
- **Logic**: Shared with all other platforms.
- **UI**: Shared Compose UI.
