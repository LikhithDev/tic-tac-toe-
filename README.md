#include <stdio.h>
#include <stdlib.h>

char board[3][3];
int x, y, i;

void printfboard() {
    printf(" %c     | %c      |  %c  \n", board[0][0], board[0][1], board[0][2]);
    printf("---    | ---    |  --- \n");
    printf(" %c     | %c      |  %c  \n", board[1][0], board[1][1], board[1][2]);
    printf("---    | ---    |  --- \n");
    printf(" %c     | %c      |  %c  \n", board[2][0], board[2][1], board[2][2]);
    printf("---    | ---    |  --- \n");
}

int Xwinnerchecker() {
    // Check for 'X' winner
    if ((board[0][0] == 'X' && board[0][1] == 'X' && board[0][2] == 'X') ||
        (board[1][0] == 'X' && board[1][1] == 'X' && board[1][2] == 'X') ||
        (board[2][0] == 'X' && board[2][1] == 'X' && board[2][2] == 'X') ||
        (board[0][0] == 'X' && board[1][1] == 'X' && board[2][2] == 'X') ||
        (board[0][2] == 'X' && board[1][1] == 'X' && board[2][0] == 'X') ||
        (board[0][0] == 'X' && board[1][0] == 'X' && board[2][0] == 'X') ||
        (board[0][1] == 'X' && board[1][1] == 'X' && board[2][1] == 'X') ||
        (board[0][2] == 'X' && board[1][2] == 'X' && board[2][2] == 'X')) {
        printf("X IS THE WINNER\n");
        return 1;
    }
    return 0;
}

int Owinnerchecker() {
    // Check for 'O' winner
    if ((board[0][0] == 'O' && board[0][1] == 'O' && board[0][2] == 'O') ||
        (board[1][0] == 'O' && board[1][1] == 'O' && board[1][2] == 'O') ||
        (board[2][0] == 'O' && board[2][1] == 'O' && board[2][2] == 'O') ||
        (board[0][0] == 'O' && board[1][1] == 'O' && board[2][2] == 'O') ||
        (board[0][2] == 'O' && board[1][1] == 'O' && board[2][0] == 'O') ||
        (board[0][0] == 'O' && board[1][0] == 'O' && board[2][0] == 'O') ||
        (board[0][1] == 'O' && board[1][1] == 'O' && board[2][1] == 'O') ||
        (board[0][2] == 'O' && board[1][2] == 'O' && board[2][2] == 'O')) {
        printf("O IS THE WINNER\n");
        return 1;  // Return 1 if O wins
    }
    return 0;  // Return 0 if O doesn't win
}

void xinput() {
    // Get input for 'X'
    printf("X's turn \n");
    printf("Enter row and column (0-2):\n");
    scanf("%d %d", &x, &y);
    if (x >= 0 && x < 3 && y >= 0 && y < 3 && board[x][y] == ' ') {
        board[x][y] = 'X';  // Place 'X' if the cell is empty and valid
    } else {
        printf("Invalid move. Try again.\n");
        xinput();  // Recurse if the move is invalid
    }
}

void oinput() {
    // Get input for 'O'
    printf("O's turn \n");
    printf("Enter row and column (0-2):\n");
    scanf("%d %d", &x, &y);
    if (x >= 0 && x < 3 && y >= 0 && y < 3 && board[x][y] == ' ') {
        board[x][y] = 'O';  // Place 'O' if the cell is empty and valid
    } else {
        printf("Invalid move. Try again.\n");
        oinput();  // Recurse if the move is invalid
    }
}

int main() {
    // Initialize the board with empty spaces
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            board[i][j] = ' ';
        }
    }

    // Main game loop
    for (i = 0; i < 9; i++) {  // Maximum 9 moves in total (3x3 board)
        xinput();  // X's turn
        printfboard();  // Print the board after X's move
        if (Xwinnerchecker()) {
            break;  // End the game if X wins
        }

        oinput();  // O's turn
        printfboard();  // Print the board after O's move
        if (Owinnerchecker()) {
            break;  // End the game if O wins
        }
    }

    return 0;
}
