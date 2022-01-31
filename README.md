# Milestone-2
milestone 2: release 1 

/*This is where the program will start*/

#include <stdio.h>
#include <stdlib.h>
#include <ctype.h>
#include <time.h>

char board[3][3];
const char PLAYER = 'X';
const char COMPUTER = 'O';

/*Prototypes start here*/
void resetBoard();
void printBoard();
int checkFreeSpaces();
void playerMove();
//void computerMove();

/*These will be added into later with their body code*/
//char checkWinner();
//void printWinner(char);

int main()
{
	char winner = ' ';

	resetBoard();
	
	while (winner == ' ' && checkFreeSpaces() != 0)
	{
		printBoard();

		playerMove();

	}

	return 0;
}

//Resets the board to its starting positions
void resetBoard()
{
	for (int i = 0; i < 3; i++)
	{
		for (int j = 0; j < 3; j++)
		{
			board[i][j] = ' ';
		}
	}
}

//Prints the outline of the board and the squares
void printBoard()
{
	printf(" %c | %c | %c ", board[0][0], board[0][1], board[0][2]);
	printf("\n---|---|---\n");
	printf(" %c | %c | %c ", board[1][0], board[1][1], board[1][2]);
	printf("\n---|---|---\n");
	printf(" %c | %c | %c ", board[2][0], board[2][1], board[2][2]);
	printf("\n");
}

//Check if there are still squares open to play
int checkFreeSpaces()
{
	int freeSpaces = 9;

	for (int i = 0; i < 3; i++)
	{
		for (int j = 0; j < 3; j++)
		{
			if (board[i][j] != ' ')
			{
				freeSpaces--;
			}
		}
	}
	return freeSpaces;
}

/*Player will move as X and computer will move as O
* If player enters a space that is not free then it will print to the user 
* Invalid Space!
*/
void playerMove()
{
	int x;
	int y;

	do
	{
		printf("Enter row #(1-3): ");
		scanf("%d", &x);
		x--;
		printf("Enter column #(1-3): ");
		scanf("%d", &y);
		y--;

		if (board[x][y] != ' ')
		{
			printf("Invalid move!\n");
		}
		else
		{
			board[x][y] = PLAYER;
			break;
		}
	} while (board[x][y] != ' ');
}

//void computerMove()
