# Interfaces

As a standalone simulator, this project focuses on internal domain interfaces rather than external HTTP REST APIs.

## Internal Service Boundaries

### 1. Scheduling Interface
The scheduling engine is designed as a set of pure functions that can be easily integrated into any Kotlin project.
- **Input**: `List<Process>`
- **Output**: `Pair<List<GanttSlice>, Map<String, ProcessMetrics>>`

### 2. Memory Management State Holder
The memory module exposes a state-holding interface that the UI observes.
- **State**: `memoryBlocks: List<MemoryBlock>`, `fragmentationStats: State<FragmentationStats>`
- **Operations**: `allocateProcess()`, `deallocateProcess(id)`, `resetMemory()`

### 3. Resource Allocation Graph (RAG) Model
The deadlock detection module uses a graph-based interface.
- **Graph State**: `processes: List<String>`, `resources: List<ResourceData>`, `edges: List<Edge>`
- **Analysis**: `runSafetyCheck(...) -> SafetyResult`

## External Connectivity
Currently, the project does not expose a conventional HTTP REST API. The `:server` module serves as a foundation for potential future API development using **Ktor**.

### Shared Constants
The `:shared` module defines common configuration values used across the client and server:
- `SERVER_PORT`: 8080 (Default)
