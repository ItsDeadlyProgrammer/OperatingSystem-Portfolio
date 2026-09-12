# Setup and Deployment

This guide explains how to build and run the original project from source.

## Prerequisites
- **JDK 21**: Required for the current Gradle and Kotlin tooling.
- **Android Studio** (Latest Stable) or **IntelliJ IDEA**.
- **Kotlin Multiplatform Plugin**: Installed in your IDE.
- **Git**: For cloning the repository.

## 1. Clone the Repository
```bash
git clone https://github.com/ItsDeadlyProgrammer/OperatingSystem.git
cd OperatingSystem
```

## 2. Run on Android
1. Open the project in Android Studio.
2. Select the `composeApp` module in the run configurations.
3. Select an emulator or a physical device (Minimum SDK 24).
4. Click **Run**.
- **CLI**: `./gradlew :composeApp:installDebug`

## 3. Run on Desktop (JVM)
1. Open the project in IntelliJ IDEA or Android Studio.
2. Run the Gradle task: `:composeApp:run`
- **CLI**: `./gradlew :composeApp:run`
- **Build Installer**: `./gradlew :composeApp:packageMsi` (on Windows) or `packageDmg` (on macOS).

## 4. Run on Web (WasmJs)
1. Run the development server:
```bash
./gradlew :composeApp:wasmJsBrowserDevelopmentRun
```
2. Open your browser to: `http://localhost:8080/`



## Troubleshooting
- **Gradle Sync Issues**: Ensure your IDE is using JDK 21 in the Gradle settings.
- **Wasm Target**: Ensure you are using a modern browser (Chrome 119+, Firefox 121+) that supports WebAssembly Garbage Collection (WasmGC).
