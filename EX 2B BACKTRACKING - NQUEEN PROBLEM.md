# EX 2B BACKTRACKING - NQUEEN PROBLEM
## DATE:
## AIM:
To solve the N-Queen problem using backtracking, which places N queens on an N*N chessboard such that no two queens threaten each other.


## Algorithm
1. Take input `N` representing the size of the chessboard (N×N) and the number of queens to place.  
2. Initialize a 2D list `board` with all zeros to represent the chessboard.  
3. Define a function `isSafe` that checks if a queen can be safely placed at position `(row, col)` by checking the left row, upper-left diagonal, and lower-left diagonal.  
4. Define a recursive function `solveNQUtil` that tries to place queens column by column.  
5. If the current column index `col` is equal to or exceeds `N`, return `True` indicating all queens are placed.  
6. For each row in the current column, check if placing a queen at `(i, col)` is safe using `isSafe`.  
7. If safe, place the queen by setting `board[i][col] = 1` and recursively call `solveNQUtil` for the next column.  
8. If the recursive call returns `True`, propagate the success; otherwise, backtrack by setting `board[i][col] = 0`.  
9. If no safe position is found in the current column, return `False`.  
10. In `solveNQ`, call `solveNQUtil` with the initial board and column 0; if successful, print the board; otherwise, print that no solution exists.   

## Program:
```python
Program to implement N-Queen problem using backtracking.
Developed by: Yuvabharathi.B
Register Number:  212222230181
global N
N = int(input())
 
def printSolution(board):
    for i in range(N):
        for j in range(N):
            print(board[i][j], end = " ")
        print()
def isSafe(board, row, col):
    # Check this row on left side
    for i in range(col):
        if board[row][i] == 1:
            return False
 
    # Check upper diagonal on left side
    for i, j in zip(range(row, -1, -1),
                    range(col, -1, -1)):
        if board[i][j] == 1:
            return False
 
    # Check lower diagonal on left side
    for i, j in zip(range(row, N, 1),
                    range(col, -1, -1)):
        if board[i][j] == 1:
            return False
 
    return True
def solveNQUtil(board, col):
    if col>=N:
        return True
    for i in range(N):
        if isSafe(board,i,col)==True:
            board[i][col]=1
            if solveNQUtil(board,col+1)==True:
                return True
            board[i][col]=0
    return False

def solveNQ():
    board = [ [0, 0, 0, 0, 0, 0, 0, 0],
              [0, 0, 0, 0, 0, 0, 0, 0],
              [0, 0, 0, 0, 0, 0, 0, 0],
              [0, 0, 0, 0, 0, 0, 0, 0],
              [0, 0, 0, 0, 0, 0, 0, 0],
              [0, 0, 0, 0, 0, 0, 0, 0],
              [0, 0, 0, 0, 0, 0, 0, 0],
              [0, 0, 0, 0, 0, 0, 0, 0]]
 
    if solveNQUtil(board, 0) == False:
        print ("Solution does not exist")
        return False
 
    printSolution(board)
    return True
# Driver Code
solveNQ()
```

## Output:
![image](https://github.com/user-attachments/assets/505a78a1-ef57-4571-bb86-3e0e07ff680e)

## Result:
The N-Queens program executed successfully, and a valid board configuration was generated.
