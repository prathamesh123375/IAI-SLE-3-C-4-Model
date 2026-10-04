# SLE-3: Architectural Design — Full C4 Model

## Maze Solving & Profiling System (DFS vs BFS)

### 📌 Project Description

This SLE-3 component presents the **Full C4 Model** of the Maze Solving & Profiling System.

The system was developed to solve a maze using two uninformed search algorithms:

* Depth-First Search (DFS)
* Breadth-First Search (BFS)

The C4 model represents the system at four levels:

1. Context Diagram
2. Container Diagram
3. Component Diagram
4. Code Level Overview

---

## 1. Context Diagram — Level 1

The **Student (operator)** runs the experiment script and selects the maze size.

The system provides:

* Path found
* Nodes expanded
* Timing information

The system depends on:

* Python runtime
* `cProfile`
* `time.perf_counter()`
* Matplotlib
* SLE-2 Word report

There is no database or network service.

---

## 2. Container Diagram — Level 2

The system is divided into six main containers:

### Maze Generator

The `generate_maze()` function generates a perfect maze using a randomized-DFS backtracker.

### Maze Model & Helpers

Contains the grid cells and walls.

The `neighbors()` function provides reachable cells in the fixed order:

```text
Up → Left → Down → Right
```

### Search Engine

Contains the two search algorithms:

```text
dfs_solve()
bfs_solve()
```

DFS uses a stack, while BFS uses a deque as a queue.

### Experiment Runner

The `run_experiments.py` script:

* Generates mazes.
* Runs DFS and BFS.
* Performs 5 runs for each of 3 maze sizes.
* Measures execution time using `time.perf_counter()`.

### Profiler

The profiler uses `cProfile`.

It performs 200 repeated solves of the 25×25 maze to produce profiling information for the flame graph.

### Results & Charts

The experimental results are stored in:

```text
results.json
```

The stored results are used to create charts and figures.

---

## 3. Component Diagram — Level 3

The **Search Engine** was selected for the Component Diagram because it is the heart of the system.

Its main components are:

### Frontier

Stores the cells waiting to be explored.

* DFS uses a stack.
* BFS uses a deque.

### Visited Set

Keeps track of already visited cells and prevents loops.

### Node Counter

Counts each cell when it is visited for the first time.

### Goal Test

Checks whether the current cell is the goal.

### Neighbour Expander

Gets reachable neighbouring cells using the `neighbors()` function.

### Parent Records

Stores the parent of each explored cell.

### Path Reconstructor

Follows the parent records from the goal back to the start to construct the final path.

---

## 4. Code Level Overview — Level 4

The main functions and scripts are:

```text
generate_maze()
neighbors()
dfs_solve()
bfs_solve()
run_experiments.py
```

### `generate_maze()`

Builds the random perfect maze.

### `neighbors()`

Returns reachable adjacent cells using the fixed order:

```text
Up → Left → Down → Right
```

### `dfs_solve()`

Implements iterative DFS using a list as a stack.

Returns:

```text
Path
Nodes Expanded
```

### `bfs_solve()`

Implements BFS using a deque as a queue.

Returns:

```text
Path
Nodes Expanded
```

### `run_experiments.py`

Runs the experiments for the selected maze sizes and records the results.

---

## 5. Design Decisions

The following design decisions were represented in the C4 model:

### Same Maze

Both DFS and BFS use the identical maze so that their comparison is fair.

### Same Neighbour Order

Both algorithms use the same neighbour order:

```text
Up → Left → Down → Right
```

Therefore, the main difference is the search strategy.

### Separate Timing and Profiling

Timing is performed using `time.perf_counter()`.

Profiling is performed separately using `cProfile`.

### Results Storage

The results are stored in:

```text
results.json
```

This allows charts and tables to be rebuilt without running the experiments again.

---

## 6. Conclusion

The Full C4 Model provides a structured view of the Maze Solving & Profiling System.

The four levels show the system from a high-level context down to the code-level functions.

The C4 model also shows that DFS and BFS share most of the search process, while their main difference is the Frontier data structure:

```text
DFS → Stack
BFS → Queue
```
