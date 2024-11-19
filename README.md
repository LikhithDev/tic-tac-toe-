#include <stdio.h>
#include <stdlib.h>


char board[3][3];
int x,y,i;

char printfboard(){

        printf(" %c     | %c      |  %c  ",board[0][0],board[0][1],board[0][2]);
        printf("\n---   | ---   |  --- \n");
        printf(" %c     | %c     |  %c  ",board[1][0],board[1][1],board[1][2]);
        printf("\n---   | ---   |  --- \n");
        printf(" %c     | %c      |  %c  ",board[2][0],board[2][1],board[2][2]);
        printf("\n---   | ---   |  --- \n");

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
}



char xinput(){
        printf("X chance \n");
        printf("Enter row and column:\n");
        scanf("%d %d",&x,&y);
        board[x][y] = 'X';
        x = 0,y=0;
}
char oinput(){
        printf("O chance \n");
        printf("Enter row and column:\n");
        scanf("%d %d",&x,&y);
         board[x][y] = 'O';
        x = 0,y=0;
}

int main()
{

            for(i=0;i<=9;i++){

                xinput();
                printfboard();
                oinput();
                printfboard();
                Xwinnerchecker();
                Owinnerchecker();
                if(Xwinnerchecker == 1 || Owinnerchecker == 1){
                    break;
                }


            }

    return 0;
}
