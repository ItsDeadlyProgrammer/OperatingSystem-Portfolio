# Algorithms Reference

This document provides a technical overview of the Operating System algorithms implemented in the project. All algorithms are implemented in pure Kotlin within the `commonMain` source set, ensuring identical behavior across all platforms.

## 1. CPU Scheduling Algorithms

The scheduling engine processes a list of `Process` models and produces a `GanttChart` (list of time slices) and `ProcessMetrics`.

### First-Come, First-Served (FCFS)
- **Type**: Non-preemptive.
- **Logic**: Processes are executed in the order of their arrival time.
- **Metrics**: Calculates Finish Time, Turnaround Time, and Waiting Time for each process.

### Shortest Job First (SJF)
- **Type**: Non-preemptive.
- **Logic**: Among arrived processes, the one with the shortest burst time is selected next.
- **Tie-breaking**: Arrival time, then Process ID.

### Shortest Remaining Time First (SRTF)
- **Type**: Preemptive (SJF).
- **Logic**: At each time unit, the process with the shortest remaining burst time is selected.
- **Preemption**: Occurs when a new process arrives with a shorter remaining time than the currently running process.

### Round Robin (RR)
- **Type**: Preemptive.
- **Logic**: Each process is given a fixed time slice (quantum) in a cyclic queue.
- **Implementation**: Uses an `ArrayDeque` to manage the ready queue and handles arrivals during execution cycles.

### Priority Scheduling
- **Type**: Both Preemptive and Non-Preemptive implementations.
- **Logic**: Processes are selected based on a priority value (lower value = higher priority).
- **Preemption**: In the preemptive version, a new arrival can preempt the current process if it has a higher priority.

---

## 2. Deadlock Detection & Avoidance

The deadlock module analyzes a **Resource Allocation Graph (RAG)** consisting of Process nodes and Resource nodes (potentially multi-instance).

### Banker's Algorithm (Safety Check)
- **Purpose**: To determine if the system is in a "Safe State".
- **Logic**: 
    1. Simulates the allocation of resources to satisfy process requests.
    2. Identifies a **Safe Sequence** where all processes can complete and release their resources.
- **Detection**: If no safe sequence exists, the system is flagged as being in a deadlocked or unsafe state.
- **Input**: Current allocations (R → P edges) and current requests (P → R edges).

---

## 3. Continuous Memory Management

The memory module simulates a fixed-size memory space (default 256 KB) managed through partitioning and coalescing.

### Allocation Strategies
- **First Fit**: Allocates the first free block that is large enough.
- **Best Fit**: Allocates the smallest free block that is large enough (minimizes wasted space in the block).
- **Worst Fit**: Allocates the largest free block available (leaves behind larger remaining fragments).
- **Next Fit**: Similar to First Fit, but starts searching from the location of the last successful allocation.

### Memory Operations
- **Allocation**: Splitting a free block into an "Allocated" block and a "Remaining Free" block.
- **Deallocation**: Converting an allocated block back to free.
- **Coalescing**: Automatically merging adjacent free blocks into a single larger block to reduce external fragmentation.

### Metrics & Fragmentation
- **Internal Fragmentation**: calculated based on unused space within an allocated partition (though simplified to 0 in the current basic block model).
- **External Fragmentation**: Calculated as the total free memory minus the size of the largest single free block.
