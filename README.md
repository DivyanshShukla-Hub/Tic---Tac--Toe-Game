  # Tic---Tac--Toe-Game

 let see my code 

     #include <stdio.h>
     #include <stdlib.h> 
     
      char board[3][3];
   
    const char PLAYER_X = 'X';  
    const char PLAYER_O = 'O';

    void resetBoard();
    void printBoard();
      int checkFreeSpaces();
      void playerMove(char player); 
      char checkWinner(); 
     void printWinner(char winner);  
 
 
    int main() { 
    char winner = ' ';
    
    resetBoard();

    while (winner == ' ' && checkFreeSpaces() != 0) {
        printBoard();
        
        
        playerMove(PLAYER_X);
        winner = checkWinner();
        if (winner != ' ' || checkFreeSpaces() == 0) {
            break;
        }

        printBoard();

        playerMove(PLAYER_O);
        winner = checkWinner();
        if (winner != ' ' || checkFreeSpaces() == 0) {
            break;
        }
    }

    printBoard();
    printWinner(winner);

    return 0;
     }

    
    void resetBoard() {
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            board[i][j] = (i * 3 + j) + '1';
        }
    }
    }

  
    void printBoard() {
    printf("\n");
    printf(" Tic Tac Toe\n");
    printf("---|---|---\n");
    for (int i = 0; i < 3; i++) {
         printf(" %c | %c | %c ", board[i][0], board[i][1], board[i][2]);
        if (i < 2) {
             printf("\n---|---|---\n");
        }
    }
    printf("\n\n");
    }


    int checkFreeSpaces() {
    int freeSpaces = 9;
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            if (board[i][j] == PLAYER_X || board[i][j] == PLAYER_O) {
                freeSpaces--; 
            }
        }
    }
    return freeSpaces;
    }


    void playerMove(char player) {
    int choice;
    int row, col;

    do {
        printf("Player %c, enter a number (1-9): ", player);
        scanf("%d", &choice);

       
        row = (choice - 1) / 3;
        col = (choice - 1) % 3;

        if (choice < 1 || choice > 9) {
            printf("Invalid input! Please choose a number between 1 and 9.\n");
        } else if (board[row][col] == PLAYER_X || board[row][col] == PLAYER_O) {
            printf("That spot is already taken! Try again.\n");
        } else {
            board[row][col] = player;
            break;
        }
    } while (1); // Loop until a valid move is made
    }

   
    char checkWinner() {
   
    for (int i = 0; i < 3; i++) {
        if (board[i][0] == board[i][1] && board[i][1] == board[i][2]) {
            return board[i][0];
        }
    }
    for (int i = 0; i < 3; i++) {
        if (board[0][i] == board[1][i] && board[1][i] == board[2][i]) {
            return board[0][i];
        }
    }

    if (board[0][0] == board[1][1] && board[1][1] == board[2][2]) {
        return board[0][0];
    }
    if (board[0][2] == board[1][1] && board[1][1] == board[2][0]) {
        return board[0][2];
    }

    return ' '; 
    }

  
     void printWinner(char winner) {
    if (winner == PLAYER_X || winner == PLAYER_O) {
        printf("Player %c wins! Congratulations!\n", winner);
    } else {
        printf("It's a draw! Good game.\n");
    }
    }
    
  THANK YOU FOOR READING
  DIVYANSH SHUKLA   
