#include<iostream>
using namespace std;
// Global Variables Defined
const int n = 3;
char arr[n][n] = { {'1','2','3'},{'4','5','6'},{'7','8','9'} };
char move = '/';
int i, j;
bool draw = false;
// Functions Defined
void printTable();
void playersMove();
bool gameEnded();

int main()
{
	// Calling Functions
    while (gameEnded())
	{
        printTable();
        playersMove();
        printTable();
        gameEnded();
    }
    if (move == '/' && draw == false) {
        cout << " PlayerB Wins." << endl;
    }
    else if (move == '*'  && draw == false) {
        cout << "PlayerA Wins. " << endl;
    }
    else {
        cout << " Game is Drawn. " << endl;
    }
    
    return 0;
}

void printTable() 
{
	// Printing Tic Tac Toe Table
    system("cls");
    cout << " Tic Tac Toe Game: " << endl;
    cout << " PlayerA[/]: " << endl;
    cout << " PlayerB[*]: " << endl;
    cout << "     |     |     " << endl;
    cout << "  " << arr[0][0] << "  |  " << arr[0][1] << "  |  " << arr[0][2] << endl;
    cout << "_____|_____|_____" << endl;
    cout << "     |     |     " << endl;
    cout << "  " << arr[1][0] << "  |  " << arr[1][1] << "  |  " << arr[1][2] << endl;
    cout << "_____|_____|_____" << endl;
    cout << "     |     |     " << endl;
    cout << "  " << arr[2][0] << "  |  " << arr[2][1] << "  |  " << arr[2][2] << endl;
    cout << "     |     |     " << endl;
}

void playersMove() {
    int choice;
    if (move == '/') 
	{
        cout << " PlayersA move: " << endl;
        cin >> choice;
    }
    else if (move == '*') 
	{
        cout << " PlayersB move: " << endl;
        cin >> choice;
    }
    switch (choice)
    {
    case 1:
	 i = 0; j = 0;
	  break;
    case 2: 
	 i = 0; j = 1; 
	  break;
    case 3: 
	 i = 0; j = 2; 
	  break;
    case 4:
	 i = 1; j = 0;
	  break;
    case 5:
	 i = 1; j = 1;
	  break;
    case 6:
	 i = 1; j = 2;
	  break;
    case 7:
	 i = 2; j = 0;
	  break;
    case 8:
	 i = 2; j = 1;
	  break;
    case 9:
	 i = 2; j = 2;
	  break;
    default:
        cout << " Invalid move. " << endl;
    }
    if (move == '/' && arr[i][j] != '/' && arr[i][j] != '*') 
	{
        arr[i][j] = '/';
        move = '*';
    }
    else if (move == '*' && arr[i][j] != '/' && arr[i][j] != '*') 
	{
        arr[i][j] = '*';
        move = '/';
    }
    else 
	{
        playersMove();
    }
}

bool gameEnded()
{
    for (int i = 0; i < n; i++)
	 {
	 	// When game is won by any Player
        if(arr[0][0] == arr[0][1] && arr[0][0] == arr[0][2] // first row
		|| arr[1][0] == arr[1][1] && arr[1][0] == arr[1][2] // second row
		|| arr[2][0] == arr[2][1] && arr[2][0] == arr[2][2] // third row
		|| arr[0][0] == arr[1][0] && arr[0][0] == arr[2][0] // first coloumn
		|| arr[0][2] == arr[1][2] && arr[0][2] == arr[2][2] // third coloumn
		|| arr[0][1] == arr[1][1] && arr[0][1] == arr[2][1] // second coloumn
		|| arr[0][0] == arr[1][1] && arr[0][0] == arr[2][2] // right diagonal
		|| arr[0][2] == arr[1][1] && arr[0][2] == arr[2][0]) // left diagonal
		
		return false;
     }
     // When game is still going on
    for (int i = 0; i < n; i++)
    {
    for (int j = 0; j < n; j++)
    {
        if (arr[i][j] != '/' && arr[i][j] != '*')
		{
            return true;
        }
    }
    }
    // When game is drawn
    draw = true;
    return false;
}
