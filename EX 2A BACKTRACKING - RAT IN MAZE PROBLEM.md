# EX 2A BACKTRACKING - RAT IN MAZE PROBLEM
## DATE:
## AIM:
To implement the Rat in a Maze problem using backtracking and find all possible paths from the start to the destination in a given maze.


## Algorithm
1. **Initialize Maze**: Create a 2D array `maze[N][N]` with open paths (`1`) and blocked paths (`0`).
2. **Initialize Solution Matrix**: Create a 2D array `sol[N][N]` to store the solution, initialized to `0`.
3. **Define `isSafe(x, y)`**: Check if the position `(x, y)` is within bounds and open.
4. **Define `solveMaze()`**: Initialize the solution matrix and call `solveMazeUtil()` to start solving.
5. **Define `solveMazeUtil(x, y)`**: Recursively try to find a path from `(x, y)` to `(N-1, N-1)`.
6. **Base Case**: If `(x, y)` is the destination, mark `sol[x][y] = 1` and return `True`.
7. **Check Safety**: If `(x, y)` is safe, mark it as part of the solution (`sol[x][y] = 1`).
8. **Move Right**: Recursively try to move right by calling `solveMazeUtil(x, y+1)`.
9. **Move Down**: If right is blocked, recursively try to move down by calling `solveMazeUtil(x+1, y)`.
10. **Backtrack**: If both right and down are blocked, backtrack by setting `sol[x][y] = 0` and return `False`.

 
## Program:
```python
Program to implement Rat in a Maze.
Developed by: Yuvabharathi.B
Register Number:  212222230181
N = 4
def printSolution( sol ):
    for i in sol:
        for j in i:
            print(str(j) + " ", end ="")
        print("")
 
def isSafe( maze, x, y ):
    if x >= 0 and x < N and y >= 0 and y < N and maze[x][y] == 1:
        return True
    return False

def solveMaze( maze ):
    # Creating a 4 * 4 2-D list
    sol = [ [ 0 for j in range(4) ] for i in range(4) ]
    if solveMazeUtil(maze, 0, 0, sol) == False:
        print("Solution doesn't exist");
        return False
    printSolution(sol)
    return True
def solveMazeUtil(maze, x, y, sol):
    if x==N-1 and y==N-1:
        sol[x][y]=1
        return True
    if isSafe(maze,x,y)==True:
        sol[x][y]=1
        if solveMazeUtil(maze,x+1,y,sol)==True:
            return True
        if solveMazeUtil(maze,x,y+1,sol)==True:
            return True
        sol[x][y]=0
        return False
if __name__ == "__main__":
    # Initialising the maze
    maze = [ [1, 0, 0, 0],
             [1, 1, 0, 1],
             [0, 1, 0, 0],
             [1, 1, 1, 1] ]
              
    solveMaze(maze)
```

## Output:
![image](https://github.com/user-attachments/assets/a6ba080e-bcb7-490c-869e-eea3d547dacf)

## Result:
The Rat in a Maze program executed successfully, and a valid path from the start to the destination was found and display.
