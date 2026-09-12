# Technical Overview

This project serves as a demonstration of high-level Kotlin Multiplatform development, focusing on complex state management and cross-platform UI consistency.

## Core Technologies

### Kotlin Multiplatform (KMP)
KMP is used to share 100% of the domain logic, data models, and algorithms between Android, Desktop, and Web. This significantly reduces development time and ensures that the core "Operating System" logic is identical regardless of the user's device.

### Compose Multiplatform
The UI is built entirely with Jetpack Compose (Multiplatform). This allows for a single codebase to define the visual representation of the simulator.
- **Canvas API**: Extensively used for custom-drawn components like the Gantt Chart and the Resource Allocation Graph.
- **Material 3**: The design system used for a modern, responsive look and feel.

### State Management
The application uses a **State-Driven UI** pattern:
- **State Holders**: Classes like `MemoryManagementStateHolder` encapsulate the logic and state (using `mutableStateOf`) for specific features.
- **Reactive Updates**: UI components automatically recompose when the underlying state (e.g., the list of processes or memory blocks) changes.

## Performance Engineering
- **Algorithm Efficiency**: Scheduling and safety algorithms are implemented using efficient Kotlin collections and data structures (e.g., `ArrayDeque`, `MutableMap`).
- **Deferred Calculation**: Complex metrics and safety sequences are calculated using `derivedStateOf` in Compose, ensuring they only re-calculate when their dependencies change.

## Platform Implementation Details

### Android
- Leverages `androidx-activity-compose` for the entry point.
- Standard Android APK packaging.

### Desktop (JVM)
- Targeted for Windows (MSI), macOS (DMG), and Linux (DEB).
- Runs on the JVM, providing high performance for simulation calculations.

### Web (WasmJs)
- Compiled to WebAssembly (Wasm) for near-native performance in the browser.
- Hosted via GitHub Pages, demonstrating the portability of Kotlin logic.

## Project Maturity
- **Code Quality**: Follows clean code principles with a clear separation between UI, logic, and data.
- **Scalability**: The architecture is designed to easily add new OS modules (e.g., Disk Scheduling, Page Replacement) by following the established State Holder pattern.
