# Engineering Decisions

This document outlines the architectural and design choices made during the development of the OS Simulator.

## 1. Choice of Kotlin Multiplatform (KMP)
- **Decision**: Use KMP to share logic across Android, JVM, and Web.
- **Context**: The core value of the project lies in the algorithms (Scheduling, Deadlock, Memory). Writing these once and sharing them ensures consistency and reduces bugs.
- **Trade-offs**: Requires a more complex project setup compared to a single-platform app, but the long-term maintainability is significantly higher.

## 2. Compose Multiplatform for UI
- **Decision**: Use Jetpack Compose for all platforms.
- **Context**: Allows for a single, declarative UI codebase. This is especially beneficial for custom visualizations (Canvas) which would otherwise need to be implemented separately for each platform's drawing API.
- **Implementation**: Used the `commonMain` source set to define 99% of the UI.

## 3. State-Driven Architecture (MVVM/State Holder)
- **Decision**: Encapsulate feature logic into State Holder classes rather than putting logic directly in Composables.
- **Context**: Improves testability and separation of concerns. The algorithms are kept as pure functions, while the State Holders manage the mutable state and interaction logic.
- **Implementation**: `MemoryManagementStateHolder`, `SchedulingViewmodel`, etc.

## 4. WasmJs for Web Target
- **Decision**: Use the experimental `wasmJs` target for the web.
- **Context**: Wasm provides better performance for computational tasks (like the Banker's algorithm or SRTF scheduling) compared to traditional JS transpilations. It also represents the cutting edge of Kotlin development.

## 5. Simplified Internal Fragmentation Model
- **Decision**: The current memory model assumes processes fit exactly into allocated partitions or uses a basic block model.
- **Context**: Simplifies the initial visualization for educational purposes. 
- **Future implementation**: A more complex paging or segmentation model could be added by extending the `MemoryBlock` data structure.

## 6. Centralized Algorithm Engine
- **Decision**: Placing algorithms in a dedicated `algorithms` package in `commonMain`.
- **Context**: Makes the "brain" of the application easy to find and verify. It ensures that the simulation logic is decoupled from the UI framework, allowing for potential CLI or backend usage (as seen in the `:server` module).
