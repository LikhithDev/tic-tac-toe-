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

    if ((board[0][0] == 'O' && board[0][1] == 'O' && board[0][2] == 'O') ||
        (board[1][0] == 'O' && board[1][1] == 'O' && board[1][2] == 'O') ||
        (board[2][0] == 'O' && board[2][1] == 'O' && board[2][2] == 'O') ||
        (board[0][0] == 'O' && board[1][1] == 'O' && board[2][2] == 'O') ||
        (board[0][2] == 'O' && board[1][1] == 'O' && board[2][0] == 'O') ||
        (board[0][0] == 'O' && board[1][0] == 'O' && board[2][0] == 'O') ||
        (board[0][1] == 'O' && board[1][1] == 'O' && board[2][1] == 'O') ||
        (board[0][2] == 'O' && board[1][2] == 'O' && board[2][2] == 'O')) {
        printf("O IS THE WINNER\n");
        return 1;
    }
    return 0;
}

void xinput() {

    printf("X's turn \n");
    printf("Enter row and column (0-2):\n");
    scanf("%d %d", &x, &y);
    if (x >= 0 && x < 3 && y >= 0 && y < 3 && board[x][y] == ' ') {
        board[x][y] = 'X';
    } else {
        printf("Invalid move. Try again.\n");
        xinput();
}

void oinput() {

    printf("O's turn \n");
    printf("Enter row and column (0-2):\n");
    scanf("%d %d", &x, &y);
    if (x >= 0 && x < 3 && y >= 0 && y < 3 && board[x][y] == ' ') {
        board[x][y] = 'O';
    } else {
        printf("Invalid move. Try again.\n");
        oinput();
    }
}

int main() {

    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            board[i][j] = ' ';
        }
    }

    for (i = 0; i < 9; i++) {
        xinput();
        printfboard();
        if (Xwinnerchecker()) {
            break;
        }

        oinput();
        printfboard();
        if (Owinnerchecker()) {
            break;
        }
    }

    return 0;
}
