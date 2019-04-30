#include <iostream> 
using namespace std;
void PrintMessage(string message, bool printTop = true, bool printBottom = true)
{
    if (printTop)
    {
        cout << "+---------------------------------+" << endl;
        cout << "|";
    }
    else
    {
        cout << "|";
    }
    bool front = true;
    for(int i = message.length(); i < 33; i++)
    {
        if (front)
        {
            message = " " + message;
        }
        else
        {
            message = message + " ";
        }
        front = !front;
    }
    cout << message.c_str();
    
     if (printBottom)
    {
        cout << "|" << endl;
        cout << "+---------------------------------+" << endl;
    }
        else
    {
        cout << "|" << endl;
    }
}
void DrawHangman(int guessCount = 0)
{
    if(guessCount >= 1)
        PrintMessage("|", false, false);
    else
        PrintMessage("", false, false);
    if(guessCount >= 2)
        PrintMessage("|", false, false);
    else
        PrintMessage("", false, false);
    if(guessCount >= 3)
        PrintMessage("O", false, false);
    else
        PrintMessage("", false, false);
    if(guessCount == 4)
        PrintMessage("/", false, false);
    if(guessCount == 5)
        PrintMessage("/|", false, false);
    if(guessCount >= 6)
        PrintMessage("/|\\", false, false);
    else
        PrintMessage("", false, false);
    if(guessCount >= 7)
        PrintMessage("|", false, false);
    else
        PrintMessage("", false, false);
    if(guessCount == 8)
        PrintMessage("/", false, false);
    if(guessCount >= 9)
        PrintMessage("/ \\", false, false);
    else
        PrintMessage("", false, false);
}
void PrintLetters(string input, char from, char to)
{
    string s;
    for(char i = from; i <= to; i++)
    {
        if(input.find(i) == string::npos)
        {
            s += i;
            s += " ";
        }
        else
            s += "  ";
    }
    PrintMessage(s, false, false);
}
void PrintAvailableLetters(string taken)
{
    PrintMessage("Available letter");
    PrintLetters(taken, 'A', 'M');
    PrintLetters(taken, 'N', 'Z');
}
bool PrintWordAndCheckWin(string word, string guessed)
{
    bool won = true;
    string s;
    for(int i = 0; i < word.length(); i++)
    {
        if(guessed.find(word[i]) == string::npos)
        {
            won = false;
            s += "_ ";
        }
        else
        {
            s += word[i];
            s += " ";
        }
    }
    PrintMessage(s, false);
    return won;
}
int main ()
{
    string guesses = "ABHJIKL";
    
    PrintMessage("HANG MAN");
    DrawHangman(9);
    PrintAvailableLetters(guesses);
    PrintMessage("Guess the word");
    PrintWordAndCheckWin("ALEXIS", guesses);
    getchar();
    return 0;
}

/*
+---------------------------------+
|            HANG MAN             |
+---------------------------------+
|                |                |
|                |                |
|                O                |
|               /|\               |
|                |                |
|               / \               |
|          +-----------+          |
|          |           |          |
+---------------------------------+
|        Available letters        |
+---------------------------------+
|    A B C D E F G H I J K L M    |
|    N O P Q R S T U V W X Y Z    |
|        Guess the word           |
+---------------------------------+
| _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ |
+---------------------------------+
*/
