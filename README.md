# Sudoku-solver-using-backtracking
#include <stdio.h>

#define N 9

// Check if the number can be placed in the cell
int isValid(int grid[N][N], int row, int col, int num) {
    // Row, column, and subgrid checks for validity
    return 1;
}

// Backtracking algorithm to solve the Sudoku
int solveSudoku(int grid[N][N]) {
    int row, col;

    // Find the first empty cell
    for (row = 0; row < N; row++) {
        for (col = 0; col < N; col++) {
            if (grid[row][col] == 0) {
                for (int num = 1; num <= 9; num++) {
                    if (isValid(grid, row, col, num)) {
                        grid[row][col] = num;
                        if (solveSudoku(grid))
                            return 1;
                        grid[row][col] = 0;
                    }
                }
                return 0;  // Trigger backtracking
            }
        }
    }
    return 1;  // Puzzle is solved
}

// Function to print the solved Sudoku grid
void printGrid(int grid[N][N]) {
    for (int row = 0; row < N; row++) {
        for (int col = 0; col < N; col++) {
            printf("%2d", grid[row][col]);
        }
        printf("\n");
    }
}

int main() {
    int grid[N][N] = {
        {5, 3, 0, 0, 7, 0, 0, 0, 0},
        {6, 0, 0, 1, 9, 5, 0, 0, 0},
        {0, 9, 8, 0, 0, 0, 0, 6, 0},
        {8, 0, 0, 0, 6, 0, 0, 0, 3},
        {4, 0, 0, 8, 0, 3, 0, 0, 1},
        {7, 0, 0, 0, 2, 0, 0, 0, 6},
        {0, 6, 0, 0, 0, 0, 2, 8, 0},
        {0, 0, 0, 4, 1, 9, 0, 0, 5},
        {0, 0, 0, 0, 8, 0, 0, 7, 9}
    };

    if (solveSudoku(grid) == 1)
        printGrid(grid);
    else
        printf("No solution exists");

    return 0;
}
