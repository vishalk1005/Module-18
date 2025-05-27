# Ex. No: 18E - Count the Number of Triangles in an Undirected Graph

## AIM:
To write a Python program to **count the number of triangles** present in an **undirected graph** using matrix operations.

## ALGORITHM:

**Step 1**: Initialize a matrix `aux2` to store the square of the adjacency matrix (i.e., `graph²`).  
Also, initialize a matrix `aux3` to store the cube of the adjacency matrix (i.e., `graph³`).

**Step 2**: Multiply the adjacency matrix with itself to compute `aux2 = graph × graph`.

**Step 3**: Multiply `aux2` with the adjacency matrix again to compute `aux3 = aux2 × graph`.

**Step 4**: Compute the **trace** of the matrix `aux3` (i.e., the sum of diagonal elements of the matrix).

**Step 5**: Divide the trace by **6** to get the number of triangles in the graph.  
*(Each triangle is counted six times in the trace — twice per vertex and once per direction.)*

**Step 6**: Return the result.

## PYTHON PROGRAM

```

import numpy as np

def count_triangles(graph):
    adj_matrix = np.array(graph)

    aux2 = np.matmul(adj_matrix, adj_matrix)
    aux3 = np.matmul(aux2, adj_matrix)

    trace = np.trace(aux3)
    triangle_count = trace // 6

    return triangle_count

graph = [
    [0, 1, 1, 0],
    [1, 0, 1, 1],
    [1, 1, 0, 1],
    [0, 1, 1, 0]
]

print("Number of triangles:", count_triangles(graph))

```

## OUTPUT

![image](https://github.com/user-attachments/assets/a1128ce5-68fb-4580-8b98-32ec9387f2a7)

## RESULT
Thus, the python function to accept a string, identify a word to be replaced, and replace it with a new word provided by the user has been executed and verified successfully.
