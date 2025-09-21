# My-Tic-Tac-Toe-program
This is my first ever tic tac toe program as a beginner programmer in c++ i know that its bot efficent clean etc but thats the best i could do

#include <iostream>
#include <vector>
#include <ctime>
#include <conio.h>
#include <algorithm>

using namespace std;

void drawboard(char board[][3]);
void userturn(char USER, char COMP, char board[][3]);
void compturn(char USER, char COMP, char board[][3]);
int checkwinner(char USER, char COMP, char board[][3]);

int main ()
{
    char USER = 'O';
    char COMP = 'X';
    char  board[][3] = {{'0', '1', '2'},
                        {'3', '4', '5'},
                        {'6', '7', '8'}};
    int winner = 5;
    int moves = 0;
    cout << "***********************\n";
    cout << "WELCOME TO TIC TAC TOE!\n";
    cout << "***********************\n";
    drawboard(board);
    while (true)
    {
        userturn(USER, COMP, board);
        drawboard(board);
        moves++;
        winner = checkwinner(USER, COMP, board);
        if (winner == 1) {
            cout << "You won!";
            break;
        }
        if (moves == 9) {
            cout << "Its a draw!";
            break;
        }
        compturn(USER, COMP, board);
        moves++;
        winner = checkwinner(USER, COMP, board);
        if(winner == 2){
            cout << "You lost!";
            break;
        }
        if (moves == 9){
            cout << "Its a draw!";
            break;
        }
    }
    return 0;
}
void drawboard(char board[][3])
{
   cout << "-----\n";
   cout << board[0][0] << "|" << board[0][1] << "|" << board[0][2] << endl;
   cout << board[1][0] << "|" << board[1][1] << "|" << board[1][2] << endl;
   cout << board[2][0] << "|" << board[2][1] << "|" << board[2][2] << endl;
   cout << "-----\n";
}
void userturn(char USER, char COMP, char board[][3])
{
    string userin;
    cout << "It's Your turn:\n";
    cout << "Enter a number from the table:\n";
    cin >> userin;
    bool occupiedin = false;
    while (userin != "0" && userin != "1" && userin != "2" && userin != "3" && userin != "4" && userin != "5" && userin != "6" && userin != "7" && userin != "8")
    {
        cout << "Please Enter a Number from the board:\n";
        cin >> userin;
    }
    if (userin == "0" && board[0][0] != COMP && board[0][0] != USER)
    {
        board[0][0] = USER;
        return;
    }
    else if (userin == "1" && board[0][1] != COMP && board[0][1] != USER)
    {
        board[0][1] = USER;
        return;
    }
    else if (userin == "2" && board[0][2] != COMP && board[0][2] != USER)
    {
        board[0][2] = USER;
        return;
    }
    else if (userin == "3" && board[1][0] != COMP && board[1][0] != USER)
    {
        board[1][0] = USER;
        return;
    }
    else if (userin == "4" && board[1][1] != COMP && board[1][1] != USER)
    {
        board[1][1] = USER;
        return;
    }
    else if (userin == "5" && board[1][2] != COMP && board[1][2] != USER)
    {
        board[1][2] = USER;
        return;
    }
    else if (userin == "6" && board[2][0] != COMP && board[2][0] != USER)
    {
        board[2][0] = USER;
        return;
    }
    else if (userin == "7" && board[2][1] != COMP && board[2][1] != USER)
    {
        board[2][1] = USER;
        return;
    }
    else if (userin == "8" && board[2][2] != COMP && board[2][2] != USER)
    {
        board[2][2] = USER;
        return;
    }
    else
    {
        occupiedin = true;
    }
    while(occupiedin == true)
    {
        cout << "Please Enter a non occupied position:";
        cin >> userin;
        cout << '\n';
    if (userin == "0" && board[0][0] != COMP && board[0][0] != USER)
    {
        board[0][0] = USER;
        occupiedin = false;
        return;
    }
    else if (userin == "1" && board[0][1] != COMP && board[0][1] != USER)
    {
        board[0][1] = USER;
        occupiedin = false;
        return;
    }
    else if (userin == "2" && board[0][2] != COMP && board[0][2] != USER)
    {
        board[0][2] = USER;
        occupiedin = false;
        return;
    }
    else if (userin == "3" && board[1][0] != COMP && board[1][0] != USER)
    {
        board[1][0] = USER;
        occupiedin = false;
        return;
    }
    else if (userin == "4" && board[1][1] != COMP && board[1][1] != USER)
    {
        board[1][1] = USER;
        occupiedin = false;
        return;
    }
    else if (userin == "5" && board[1][2] != COMP && board[1][2] != USER)
    {
        board[1][2] = USER;
        occupiedin = false;
        return;
    }
    else if (userin == "6" && board[2][0] != COMP && board[2][0] != USER)
    {
        board[2][0] = USER;
        occupiedin = false;
        return;
    }
    else if (userin == "7" && board[2][1] != COMP && board[2][1] != USER)
    {
        board[2][1] = USER;
        occupiedin = false;
        return;
    }
    else if (userin == "8" && board[2][2] != COMP && board[2][2] != USER)
    {
        board[2][2] = USER;
        occupiedin = false;
        return;
    }
    }
}
void compturn(char USER, char COMP, char board[][3])
{
    cout << "computer's turn:\n";
    //for playing win
    for(int i = 0 ;i < 3 ; i++)
    {
        //left and right taken by comp middle empty
        if(board[i][0] == COMP && board[i][2] == COMP && board[i][1] != USER && board[i][1] != COMP) 
        {
            board[i][1] = COMP;
            drawboard(board);
            return;
        }
        //left and middle taken by comp right empty
        if(board[i][0] == COMP && board[i][1] == COMP && board[i][2] != USER && board[i][2] != COMP) 
        {
            board[i][2] = COMP;
            drawboard(board);
            return;
        }
        //middle and right take by comp left empty
        if(board[i][1] == COMP && board[i][2] == COMP && board[i][0] != USER && board[i][0] != COMP) 
        {
            board[i][0] = COMP;
            drawboard(board);
            return;
        }
    }
    //for vertical
    for(int j = 0 ;j < 3 ; j++)
    {
        //up and down taken by comp middle empty
        if(board[0][j] == COMP && board[2][j] == COMP && board[1][j] != USER && board[1][j] != COMP) 
        {
            board[1][j] = COMP;
            drawboard(board);
            return;
        }
        //up and middle taken by comp down empty
        if(board[0][j] == COMP && board[1][j] == COMP && board[2][j] != USER && board[2][j] != COMP) 
        {
            board[2][j] = COMP;
            drawboard(board);
            return;
        }
        //middle and down taken by comp up empty
        if(board[1][j] == COMP && board[2][j] == COMP && board[0][j] != USER && board[0][j] != COMP) 
        {
            board[0][j] = COMP;
            drawboard(board);
            return;
        }
    }
    //for diagonal
    if (board[0][0] == COMP && board[1][1] == COMP && board[2][2] != USER && board[2][2] != COMP) 
    {
        board[2][2] = COMP;
        drawboard(board);
        return;
    }
    if (board[0][0] == COMP && board[2][2] == COMP && board[1][1] != USER && board[1][1] != COMP) 
    {
        board[1][1] = COMP;
        drawboard(board);
        return;
    }
    if (board[1][1] == COMP && board[2][2] == COMP && board[0][0] != USER && board[0][0] != COMP) 
    {
        board[0][0] = COMP;
        drawboard(board);
        return;
    }
    // for diagonal (top-right to bottom-left)
    if (board[0][2] == COMP && board[1][1] == COMP && board[2][0] != USER && board[2][0] != COMP) 
    {
        board[2][0] = COMP;
        drawboard(board);
        return;
    }
    if (board[0][2] == COMP && board[2][0] == COMP && board[1][1] != USER && board[1][1] != COMP) 
    {
        board[1][1] = COMP;
        drawboard(board);
        return;
    }
    if (board[1][1] == COMP && board[2][0] == COMP && board[0][2] != USER && board[0][2] != COMP) 
    {
        board[0][2] = COMP;
        drawboard(board);
        return;
    }
    //for blocking user move
    //for horizontal
    for(int i = 0 ;i < 3 ; i++)
    {
        //left and right taken by user middle empty
        if(board[i][0] == USER && board[i][2] == USER && board[i][1] != USER && board[i][1] != COMP) 
        {
            board[i][1] = COMP;
            drawboard(board);
            return;
        }
        //left and middle taken bu user right empty
        if(board[i][0] == USER && board[i][1] == USER && board[i][2] != USER && board[i][2] != COMP) 
        {
            board[i][2] = COMP;
            drawboard(board);
            return;
        }
        //middle and right take by user left empty
        if(board[i][1] == USER && board[i][2] == USER && board[i][0] != USER && board[i][0] != COMP) 
        {
            board[i][0] = COMP;
            drawboard(board);
            return;
        }
    }
    //for vertical
    for(int j = 0 ;j < 3 ; j++)
    {
        //up and down taken by user middle empty
        if(board[0][j] == USER && board[2][j] == USER && board[1][j] != USER && board[1][j] != COMP) 
        {
            board[1][j] = COMP;
            drawboard(board);
            return;
        }
        //up and middle taken by user down empty
        if(board[0][j] == USER && board[1][j] == USER && board[2][j] != USER && board[2][j] != COMP) 
        {
            board[2][j] = COMP;
            drawboard(board);
            return;
        }
        //middle and down taken by user up empty
        if(board[1][j] == USER && board[2][j] == USER && board[0][j] != USER && board[0][j] != COMP) 
        {
            board[0][j] = COMP;
            drawboard(board);
            return;
        }
    }
    //for diagonal
    if (board[0][0] == USER && board[1][1] == USER && board[2][2] != USER && board[2][2] != COMP) 
    {
        board[2][2] = COMP;
        drawboard(board);
        return;
    }
    if (board[0][0] == USER && board[2][2] == USER && board[1][1] != USER && board[1][1] != COMP) 
    {
        board[1][1] = COMP;
        drawboard(board);
        return;
    }
    if (board[1][1] == USER && board[2][2] == USER && board[0][0] != USER && board[0][0] != COMP) 
    {
        board[0][0] = COMP;
        drawboard(board);
        return;
    }
    // for diagonal (top-right to bottom-left)
    if (board[0][2] == USER && board[1][1] == USER && board[2][0] != USER && board[2][0] != COMP) 
    {
        board[2][0] = COMP;
        drawboard(board);
        return;
    }
    if (board[0][2] == USER && board[2][0] == USER && board[1][1] != USER && board[1][1] != COMP) 
    {
        board[1][1] = COMP;
        drawboard(board);
        return;
    }
    if (board[1][1] == USER && board[2][0] == USER && board[0][2] != USER && board[0][2] != COMP) 
    {
        board[0][2] = COMP;
        drawboard(board);
        return;
    }
    //for random move
    //priority (middle>corners>edges)
    vector<pair<int, int>> middles, corners, edges;
    // Middle
    if(board[1][1] != USER && board[1][1] != COMP)
        middles.push_back({1, 1});
    // Corners
    if(board[0][0] != USER && board[0][0] != COMP)
        corners.push_back({0, 0});
    if(board[0][2] != USER && board[0][2] != COMP)
        corners.push_back({0, 2});
    if(board[2][0] != USER && board[2][0] != COMP)
        corners.push_back({2, 0});
    if(board[2][2] != USER && board[2][2] != COMP)
        corners.push_back({2, 2});
    // Edges
    if(board[0][1] != USER && board[0][1] != COMP)
        edges.push_back({0, 1});
    if(board[1][0] != USER && board[1][0] != COMP)
        edges.push_back({1, 0});
    if(board[1][2] != USER && board[1][2] != COMP)
        edges.push_back({1, 2});
    if(board[2][1] != USER && board[2][1] != COMP)
        edges.push_back({2, 1});
    srand((unsigned int)time(0));
    if (!middles.empty()) {
        board[middles[0].first][middles[0].second] = COMP;
        drawboard(board);
        return;
    }
    if (!corners.empty()) {
        std::random_shuffle(corners.begin(), corners.end());
        board[corners[0].first][corners[0].second] = COMP;
        drawboard(board);
        return;
    }
    if (!edges.empty()) {
        std::random_shuffle(edges.begin(), edges.end());
        board[edges[0].first][edges[0].second] = COMP;
        drawboard(board);
        return;
    }
}

int checkwinner(char USER, char COMP, char board[][3])
{
    for(int i = 0; i < 3; i++)
    {    //for USER
         //horizontal
         if(board[i][0] == USER && board[i][1] == USER && board[i][2] == USER)
         {
            return 1;
            //1 return equals to user win
         }
         //for vertical
         else if(board[0][i] == USER && board[1][i] == USER && board[2][i] == USER)
         {
            return 1;
         }
    }
    //for diagonal
         if(board[0][0] == USER && board[1][1] == USER && board[2][2] == USER)
         {
            return 1;
         }
         else if(board[0][2] == USER && board[1][1] == USER && board[2][0] == USER)
         {
            return 1;
         }
         //for comp
    for(int j = 0; j < 3; j++)
    {
         //horizontal
         if(board[j][0] == COMP && board[j][1] == COMP && board[j][2] == COMP)
         {
            return 2;
            //2 return equals to computer win
         }
         //for vertical
         else if(board[0][j] == COMP && board[1][j] == COMP && board[2][j] == COMP)
         {
            return 2;
         }
    }
    //for diagonal
         if(board[0][0] == COMP && board[1][1] == COMP && board[2][2] == COMP)
         {
            return 2;
         }
         else if(board[0][2] == COMP && board[1][1] == COMP && board[2][0] == COMP)
         {
            return 2;
         }
         return 0;
}


