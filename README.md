# Tic---Tac--Toe-Game
let see my code

      #include <stdio.h>
     #include <stdlib.h> 

    // Global array to represent the game board
      char board[3][3];
   
    // Constants for players  
    const char PLAYER_X = 'X';
    const char PLAYER_O = 'O';

    // --- Function Prototypes ---
    void resetBoard();
    void printBoard();
      int checkFreeSpaces();
      void playerMove(char player);
      char checkWinner();
     void printWinner(char winner); 

 
    int main() {
    char winner = ' ';
    
    resetBoard();

    // Main game loop
    while (winner == ' ' && checkFreeSpaces() != 0) {
        printBoard();
        
        // Player X's turn
        playerMove(PLAYER_X);
        winner = checkWinner();
        if (winner != ' ' || checkFreeSpaces() == 0) {
            break;
        }

        printBoard();

        // Player O's turn
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

    /**
    * @brief Initializes the board with numbers 1-9.
    */
    void resetBoard() {
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            board[i][j] = (i * 3 + j) + '1';
        }
    }
    }

    /**
    * @brief Prints the current state of the game board.
    */
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

    /**
    * @brief Counts the number of empty spaces left on the board.
    * @return The number of free spaces.
     */
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

     /**
    * @brief Handles the logic for a player's turn.
    * @param player The current player ('X' or 'O').
     */
    void playerMove(char player) {
    int choice;
    int row, col;

    do {
        printf("Player %c, enter a number (1-9): ", player);
        scanf("%d", &choice);

        // Convert choice (1-9) to 2D array coordinates (0-2)
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

     /**
    * @brief Checks all win conditions (rows, columns, diagonals).
    * @return The character of the winner ('X' or 'O'), or ' ' if no winner yet.
     */
    char checkWinner() {
    // Check rows
    for (int i = 0; i < 3; i++) {
        if (board[i][0] == board[i][1] && board[i][1] == board[i][2]) {
            return board[i][0];
        }
    }
    // Check columns
    for (int i = 0; i < 3; i++) {
        if (board[0][i] == board[1][i] && board[1][i] == board[2][i]) {
            return board[0][i];
        }
    }
    // Check diagonals
    if (board[0][0] == board[1][1] && board[1][1] == board[2][2]) {
        return board[0][0];
    }
    if (board[0][2] == board[1][1] && board[1][1] == board[2][0]) {
        return board[0][2];
    }

    return ' '; // No winner
    }

    /**
    * @brief Prints the final result of the game.
     * @param winner The winning player, or ' ' for a draw.
      */
     void printWinner(char winner) {
    if (winner == PLAYER_X || winner == PLAYER_O) {
        printf("Player %c wins! Congratulations!\n", winner);
    } else {
        printf("It's a draw! Good game.\n");
    }
    }
  THANK YOU FOOR READING
  DIVYANSH SHUKLA
