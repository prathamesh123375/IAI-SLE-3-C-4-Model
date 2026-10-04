# Contribution Log
---

#  My Contribution

My contribution to SLE-3 was focused on creating and reviewing the **Full C4 Model** of my Maze Solving & Profiling System.

## 1. Context Diagram

I identified:

* The Student as the system operator.
* The Maze Solving & Profiling System as the main system.
* The Python runtime and profiling tools.
* draw.io for charts.
* The SLE-2 report as the place where results are used.

I reviewed the system boundary and its external dependencies.

---

## 2. Container Diagram

I identified the six main containers:

1. Maze Generator
2. Maze Model & Helpers
3. Search Engine
4. Experiment Runner
5. Profiler
6. Results & Charts

I matched these containers with the actual structure of my project.

---

## 3. Component Diagram

I selected the **Search Engine** for detailed component-level representation.

I identified its main components:

* Frontier
* Visited Set
* Node Counter
* Goal Test
* Neighbour Expander
* Parent Records
* Path Reconstructor

I also identified the main difference between the two search algorithms:

```text
DFS → Stack
BFS → Queue
```

---

## 4. Code Level Overview

I matched the C4 model with the actual functions and scripts:

```text
generate_maze()
neighbors()
dfs_solve()
bfs_solve()
agent.py
```

I reviewed whether the functions shown in the C4 model correctly represented the actual project.

---

## 5. Design Decisions

I reviewed and documented the important architectural decisions:

* DFS and BFS use the same maze.
* Both algorithms use the same neighbour order.
* Maze generation and searching are separated.
* Timing and profiling are kept separate.
* Results are stored in `results.json`.

---

#  AI Contribution

## AI Tool Used

**Claude (Anthropic)**

AI helped with:

* Structuring the SLE-3 document.
* Polishing the wording of the explanations.
  
---
The final C4 architecture was reviewed by me to ensure that it represented my actual system.
