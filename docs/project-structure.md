# Project Structure

The repository is organized to maximize code sharing through Kotlin Multiplatform. Below is a map of the most important directories and their purposes.

```text
OperatingSystem/
├── composeApp/                 # Main application module (Compose Multiplatform)
│   ├── src/
│   │   ├── commonMain/         # SHARED UI and LOGIC (90%+ of code)
│   │   │   ├── algorithms/     # OS Algorithm implementations (pure Kotlin)
│   │   │   ├── data/           # Domain models (Process, MemoryBlock, etc.)
│   │   │   ├── ui/             # Compose UI screens and components
│   │   │   └── viewmodel/      # State management and UI logic
│   │   ├── androidMain/        # Android-specific entry point and resources
│   │   ├── desktopMain/        # JVM-specific entry point (Main.kt)
│   │   ├── wasmJsMain/         # Web/Wasm-specific entry point
│   │   └── iosMain/            # iOS-specific entry point
│   └── build.gradle.kts        # KMP target and dependency configuration
│
├── shared/                     # Shared library module
│   ├── src/
│   │   └── commonMain/         # Basic shared utilities and platform interfaces
│   └── build.gradle.kts
│
├── server/                     # Ktor backend module
│   └── src/main/kotlin/        # Backend server implementation
│
├── gradle/                     # Gradle wrapper and version catalogs
│   └── libs.versions.toml      # Centralized dependency management
│
└── build.gradle.kts            # Root build script
```

## Key Files
- **`composeApp/src/commonMain/kotlin/algorithms/`**: Contains the core logic for CPU Scheduling.
- **`composeApp/src/commonMain/kotlin/ui/Deadlock.kt`**: Contains both the RAG visualization and the Banker's safety algorithm.
- **`composeApp/src/commonMain/kotlin/viewmodel/MemoryViewmodel.kt`**: Manages the state for memory allocation simulations.
- **`libs.versions.toml`**: Defines the versions for Kotlin, Compose, and other libraries used across all modules.
