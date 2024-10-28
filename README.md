#include <stdio.h>
#include <stdlib.h>
#include <time.h>

#define BOARD_SIZE 100

// Function to simulate rolling a die
int rollDie() {
    return (rand() % 6) + 1; // Returns a value between 1 and 6
}

// Function to get the new position after applying snakes or ladders
int getNewPosition(int position) {
    switch (position) {
        case 3: return 22; // ladder
        case 5: return 8;  // ladder
        case 11: return 26; // ladder
        case 20: return 29; // ladder
        case 17: return 4;  // snake
        case 19: return 7;  // snake
        case 21: return 9;  // snake
        case 27: return 1;  // snake
        case 38: return 43; // ladder
        case 50: return 66; // ladder
        case 72: return 84; // ladder
        case 80: return 99; // ladder
        case 91: return 75; // snake
        case 93: return 73; // snake
        case 95: return 78; // snake
        case 99: return 78; // snake
        default: return position; // no snake or ladder
    }
}

// Function to check if a player has won
int checkWin(int position) {
    return position >= BOARD_SIZE;
}

int main() {
    int player1 = 0, player2 = 0;
    int turn = 0;

    // Seed for random number generation
    srand(time(NULL));

    printf("Welcome to Snakes and Ladders!\n");

    while (1) {
        int currentPlayer = turn % 2 + 1;
        printf("Player %d's turn.\n", currentPlayer);
        
        // Roll the die
        int roll = rollDie();
        printf("Player %d rolled a %d.\n", currentPlayer, roll);
        
        if (currentPlayer == 1) {
            player1 += roll;
            player1 = getNewPosition(player1);
            printf("Player 1 is now on square %d.\n", player1);
            if (checkWin(player1)) {
                printf("Player 1 wins!\n");
                break;
            }
        } else {
            player2 += roll;
            player2 = getNewPosition(player2);
            printf("Player 2 is now on square %d.\n", player2);
            if (checkWin(player2)) {
                printf("Player 2 wins!\n");
                break;
            }
        }
        
        turn++;
        printf("\n");
    }

    return 0;
}
# sl
