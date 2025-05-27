# Ex. No: 18A - Prim's Minimum Spanning Tree (MST) Algorithm

## AIM:
To write a Python program for **Prim's Minimum Spanning Tree (MST)** algorithm.

## ALGORITHM:

**Step 1**: Initialize the `key[]` array to infinity, set the first vertex's key to `0`, and create `mstSet[]` and `parent[]` arrays.

**Step 2**: Select the vertex with the smallest key value not yet included in `mstSet`.

**Step 3**: Add the selected vertex to `mstSet`.

**Step 4**: For all adjacent vertices:
- If the edge weight is smaller than their current key value, and the vertex is not in `mstSet`, then:
  - Update their key value
  - Update their parent to the current vertex

**Step 5**: Repeat Steps 2–4 until all vertices are included in the MST.

**Step 6**: Print the resulting Minimum Spanning Tree using the `parent[]` array.

## PYTHON PROGRAM

```

import sys

class PrimMST:
    def __init__(self, graph):
        self.graph = graph
        self.V = len(graph)

    def min_key(self, key, mstSet):
        min_val = sys.maxsize
        min_index = -1
        for v in range(self.V):
            if key[v] < min_val and not mstSet[v]:
                min_val = key[v]
                min_index = v
        return min_index

    def prim_mst(self):
        key = [sys.maxsize] * self.V
        parent = [None] * self.V
        key[0] = 0
        mstSet = [False] * self.V
        parent[0] = -1

        for _ in range(self.V):
            u = self.min_key(key, mstSet)
            mstSet[u] = True

            for v in range(self.V):
                if self.graph[u][v] and not mstSet[v] and self.graph[u][v] < key[v]:
                    key[v] = self.graph[u][v]
                    parent[v] = u

        self.print_mst(parent)

    def print_mst(self, parent):
        print("Edge \tWeight")
        total_weight = 0
        for i in range(1, self.V):
            print(f"{parent[i]} - {i} \t{self.graph[i][parent[i]]}")
            total_weight += self.graph[i][parent[i]]
        print("Total weight of MST:", total_weight)

graph = [
    [0, 2, 0, 6, 0],
    [2, 0, 3, 8, 5],
    [0, 3, 0, 0, 7],
    [6, 8, 0, 0, 9],
    [0, 5, 7, 9, 0]
]

mst = PrimMST(graph)
mst.prim_mst()

```

## OUTPUT
![image](https://github.com/user-attachments/assets/1dc66e5f-fff4-4345-b495-475ed417f704)

## RESULT
Thus,the python program for Prim's Minimum Spanning Tree (MST) algorithm has been executed and verified successfully.
