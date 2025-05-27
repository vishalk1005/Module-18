# Ex. No: 18C - Dijkstra's Single Source Shortest Path Algorithm

## AIM:
To write a Python program for **Dijkstra's single source shortest path algorithm**.

## ALGORITHM:

**Step 1**: Initialize a `distance[]` array with infinity for all vertices except the source, which is set to `0`.  
Create a `sptSet[]` array (shortest path tree set) to keep track of vertices whose shortest distance from the source is finalized.

**Step 2**: Pick the vertex `u` with the minimum distance value from the set of vertices not yet processed.

**Step 3**: For every adjacent vertex `v` of the picked vertex `u`, if the current distance to `v` is greater than the distance to `u` plus the edge weight `(u, v)`, then update the distance of `v`.

**Step 4**: Mark the vertex `u` as processed in `sptSet`.

**Step 5**: Repeat Steps 2–4 until all vertices are processed.

**Step 6**: Print the shortest distances from the source to all other vertices.

## PYTHON PROGRAM

```
import sys

class Dijkstra:
    def __init__(self, graph):
        self.graph = graph
        self.V = len(graph)

    def min_distance(self, dist, sptSet):
        min_val = sys.maxsize
        min_index = -1
        for v in range(self.V):
            if dist[v] < min_val and not sptSet[v]:
                min_val = dist[v]
                min_index = v
        return min_index

    def dijkstra(self, src):
        dist = [sys.maxsize] * self.V
        dist[src] = 0
        sptSet = [False] * self.V

        for _ in range(self.V):
            u = self.min_distance(dist, sptSet)
            sptSet[u] = True
            for v in range(self.V):
                if (self.graph[u][v] > 0 and not sptSet[v] and 
                    dist[u] + self.graph[u][v] < dist[v]):
                    dist[v] = dist[u] + self.graph[u][v]

        self.print_solution(dist)

    def print_solution(self, dist):
        print("Vertex \tDistance from Source")
        for i in range(self.V):
            print(i, "\t", dist[i])

graph = [
    [0, 4, 0, 0, 0, 0, 0, 8, 0],
    [4, 0, 8, 0, 0, 0, 0, 11, 0],
    [0, 8, 0, 7, 0, 4, 0, 0, 2],
    [0, 0, 7, 0, 9, 14, 0, 0, 0],
    [0, 0, 0, 9, 0, 10, 0, 0, 0],
    [0, 0, 4, 14, 10, 0, 2, 0, 0],
    [0, 0, 0, 0, 0, 2, 0, 1, 6],
    [8, 11, 0, 0, 0, 0, 1, 0, 7],
    [0, 0, 2, 0, 0, 0, 6, 7, 0]
]

d = Dijkstra(graph)
d.dijkstra(0)

```

## OUTPUT
![image](https://github.com/user-attachments/assets/f296dc77-3440-4b8e-a175-d543e98e7381)


## RESULT
Thus, the python program for **Dijkstra's single source shortest path algorithm has been executed and verified successfully.
