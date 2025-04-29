# EX 2D BACKTRACKING - GRAPH COLORING PROBLEM
## DATE:
## AIM:
To solve the Graph Coloring Problem using backtracking, assigning colors to the vertices of a graph such that no two adjacent vertices share the same color while minimizing the number of colors used.



## Algorithm
1. Define a class `Graph` with an initializer that sets the number of vertices `V` and initializes a `V x V` adjacency matrix `graph` with all zeros.  
2. Define a function `isSafe` that checks if a given color `c` can be assigned to vertex `v` by ensuring that no adjacent vertex has the same color.  
3. Define a recursive utility function `graphColourUtil` which tries to assign colors from `1` to `m` to each vertex starting from vertex `v`.  
4. If all vertices are assigned a color (i.e., `v == V`), return `True` indicating success.  
5. For the current vertex `v`, try each color `c` from `1` to `m`:  
6. If assigning color `c` to vertex `v` is safe, assign it (`colour[v] = c`) and make a recursive call to color the next vertex.  
7. If the recursive call returns `True`, propagate success; otherwise, backtrack by resetting `colour[v] = 0`.  
8. If no color can be assigned to the current vertex, return `False`.  
9. Define the function `graphColouring` that initializes a color list with zeros and starts the coloring process by calling `graphColourUtil`.  
10. If coloring is successful, print the colors assigned to each vertex; otherwise, return `False`.   

## Program:
```python
Program to implement Graph Coloring Problem using backtracking.
Developed by: Yuvabharathi B
Register Number:  212222230181
class Graph():
    def __init__(self,vertices):
        self.V=vertices
        self.graph=[[0 for column in range(vertices)]for row in range(vertices)]
    def isSafe(self,v,colour,c):
        for i in range(self.V):
            if self.graph[v][i]==1 and colour[i]==c:
                return False
        return True
    def graphColourUtil(self,m,colour,v):
        if v==self.V:
            return True
            
        for c in range(1,m+1):
            if self.isSafe(v,colour,c)== True:
                colour[v]=c
                if self.graphColourUtil(m,colour,v+1)==True:
                    return True
                colour[v]=0
    def graphColouring(self,m):
        colour=[0]*self.V
        if self.graphColourUtil(m,colour,0)==None:
            return False
        print("Solution exist and Following are the assigned colours:")
        for c in colour:
            print(c,end=' ')
        return True
```

## Output:
![image](https://github.com/user-attachments/assets/1a0ff028-5e0a-4523-a189-c45230545885)

## Result:
The Graph Coloring program executed successfully, and the colors were assigned to the vertices such that no two adjacent vertices share the same color.
