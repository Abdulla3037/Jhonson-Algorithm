# 🛣️ Johnson's Algorithm: All-Pairs Shortest Path

This project is a console-based C++ implementation of Johnson's Algorithm. It calculates the shortest paths between every pair of vertices in a weighted directed graph including graphs that have negative edge weights as long as no negative-weight cycles exist.

---

## 📑 Table of Contents

| # | Section |
|---|---------|
| 1️⃣ | [What This Program Can Do](#-what-this-program-can-do) |
| 2️⃣ | [How The Algorithm Works](#-how-the-algorithm-works) |
| 3️⃣ | [Algorithm Flowchart](#-algorithm-flowchart) |
| 4️⃣ | [How To Run The Project](#-how-to-run-the-project) |
| 5️⃣ | [Input Format](#-input-format) |
| 6️⃣ | [Sample Output](#-sample-output) |
| 7️⃣ | [Time Complexity](#-time-complexity) |
| 8️⃣ | [Important Notes](#-important-notes) |
| 9️⃣ | [Requirements](#-requirements) |
| 🔟 | [Contributing](#-contributing) |
| 🔢 | [License](#-license) |
| 🔢 | [Contact](#-contact) |

---

## ⚡ What This Program Can Do

- Detect negative-weight cycles via the Bellman-Ford algorithm
- Re-weight all edges so none remain negative, while preserving the true shortest paths
- Compute shortest paths between every pair of vertices using Dijkstra's algorithm
- Handle graphs that contain negative edge weights (but not negative cycles)
- Display "No path" whenever no route exists between two vertices
- Exit immediately and report an error if a negative-weight cycle is found

---

## 🔎 How The Algorithm Works

Johnson's Algorithm determines the shortest path between **every pair of vertices** in a weighted directed graph. It cleverly combines Bellman-Ford and Dijkstra: Bellman-Ford runs **once** to handle any negative weights, then the faster Dijkstra handles the rest.

- **Step 1:** Introduce a temporary source node connected to all vertices with zero-weight edges
- **Step 2:** Run Bellman-Ford to compute a helper value `h[v]` for every vertex and check for negative-weight cycles
- **Step 3:** Re-weight each edge using `new weight = old weight + h[u] − h[v]` to guarantee non-negative weights
- **Step 4:** Run Dijkstra from every vertex on the re-weighted graph
- **Step 5:** Recover the true distances using `true distance = dijkstra result − h[u] + h[v]`

---

## 🗂️ Algorithm Flowchart

A detailed visual flowchart of the algorithm is included in this repository.

📄 [View Johnson's Algorithm Flowchart (PDF)](./Jhonson's%20Algorithm%20Flowchart.pdf)

---

## 🚀 How To Run The Project

### Step 1: Install Required Tools

- Install [Visual Studio Code](https://code.visualstudio.com/)
- Install the **C/C++ Extension** by Microsoft from the VS Code Extensions panel
- Install [MinGW-w64](https://www.mingw-w64.org/) and add `C:\mingw64\bin` to your system PATH

### Step 2: Open The Project

Launch VS Code, go to **File → Open Folder**, and choose the folder containing `Jhonson's Algorithm.cpp`.

### Step 3: Configure VS Code

Ensure your `.vscode/tasks.json` looks like this:

```json
{
    "version": "2.0.0",
    "tasks": [
        {
            "type": "shell",
            "label": "C/C++: g++.exe build active file",
            "command": "C:\\mingw64\\bin\\g++.exe",
            "args": [
                "-fdiagnostics-color=always",
                "-g",
                "${fileBasename}",
                "-o",
                "${fileBasenameNoExtension}.exe",
                "-static-libgcc",
                "-static-libstdc++"
            ],
            "options": {
                "cwd": "${fileDirname}"
            },
            "problemMatcher": ["$gcc"],
            "group": {
                "kind": "build",
                "isDefault": true
            }
        }
    ]
}
```

### Step 4: Compile and Run

Open `Jhonson's Algorithm.cpp` in the editor and press **Ctrl+Alt+N** to build and run. A terminal will appear at the bottom of VS Code where you can provide your input.

---

## 💻 Input Format

When the program starts, it will prompt you for:

    Vertices:
    Edges:

Then enter each directed edge on a separate line in this format:

    <source> <destination> <weight>

**Example input:**

    Vertices: 5
    Edges: 9
    0 1 3
    0 2 8
    0 3 2
    0 4 -4
    1 4 7
    1 3 1
    2 1 4
    3 2 -5
    4 3 6

- Vertices are **0-indexed**
- Edges are **directed** (one-way only)
- Negative weights are **allowed**; negative-weight cycles are **not**

---

## 🖥️ Sample Output

### When no negative cycle exists

    Shortest distance from 0 to 0 is 0
    Shortest distance from 0 to 1 is 1
    Shortest distance from 0 to 2 is -3
    Shortest distance from 0 to 3 is 2
    Shortest distance from 0 to 4 is -4
    No path from 1 to 0
    Shortest distance from 1 to 2 is -4
    Shortest distance from 1 to 3 is 1
    Shortest distance from 1 to 4 is 7
    ...

### When a negative cycle is detected

    Negative weight cycle detected

---

## ⏳ Time Complexity

| Component | Complexity |
| --- | --- |
| Bellman-Ford | O(V · E) |
| Edge Re-weighting | O(E) |
| Dijkstra (run V times) | O(V(V + E) log V) |
| **Total** | **O(V² log V + V · E)** |

---

## ⚠️ Important Notes

- Vertices must be **0-indexed**, starting from `0`.
- The algorithm only works on **directed** (one-way) graphs.
- Negative edge weights are **permitted**, but negative-weight **cycles** will cause the program to terminate early.
- The distance from any vertex to itself is always **0**.
- Always enter the correct vertex and edge counts before inputting the edges.
- The program calls `system("pause")` at the end, which **only works on Windows**. Remove this line before compiling on Linux or macOS.

---

## 🛠️ Requirements

- MinGW-w64 with `C:\mingw64\bin` added to your system PATH
- Windows OS
- Visual Studio Code with the C/C++ extension

---

## 🤝 Contributing

Have ideas or improvements? Feel free to fork the repository, apply your changes, and submit a pull request.

---

## 🔐 License

This project is licensed under the [MIT License](./LICENSE).

---

## ✉️ Contact

For any questions or concerns, feel free to reach out by email at abdullahasan220618@gmail.com
