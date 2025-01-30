# Solve-the-Sudoku-gfg
Given an incomplete Sudoku configuration in terms of a 9x9  2-D interger square matrix, mat[][], the task is to solve the Sudoku. It is guaranteed that the input Sudoku will have exactly one solution.

A sudoku solution must satisfy all of the following rules:

Each of the digits 1-9 must occur exactly once in each row.
Each of the digits 1-9 must occur exactly once in each column.
Each of the digits 1-9 must occur exactly once in each of the 9 3x3 sub-boxes of the grid.
Note: Zeros represent blanks to be filled with numbers 1-9, while non-zero cells are fixed and cannot be changed.

Examples:

Input: mat[][] = 

Output:

Explanation: Each row, column and 3 x 3 box of the output matrix contains unique numbers.
Input: mat[][] = 

Output:

Explanation: Each row, column and 3 x 3 box of the output matrix contains unique numbers.
# code
class Solution {
    // Function to find a solved Sudoku.
    static void solveSudoku(int[][] mat) {
        // code here
        helper(mat);
    }
    
    static boolean helper(int mat[][]){
        for(int i = 0; i < 9; i++){
            for(int j = 0; j < 9; j++){
                if(mat[i][j] == 0){
                    for(int k = 1; k <= 9; k++){
                        if(isValid(i,j,mat,k)){
                            mat[i][j] = k;
                            if(helper(mat)) return true;
                            else mat[i][j] = 0;
                        }
                    }
                    return false;
                }
            }
        }
        return true;
    }
    
    static boolean isValid(int row, int col, int mat[][], int k){
        for(int i = 0; i < 9; i++){
            if(mat[row][i] == k) return false;
            
            if(mat[i][col] == k) return false;
            
            if(mat[3 * (row / 3) + i / 3][3 * (col / 3) + i % 3] == k) return false;
        }
        return true;
        
    }
}
