#include <iostream>
#include <cstdlib>
#include <ctime>
#include <string>
using namespace std;
const int maxTries = 9;
int letterFill(char, string, string&);

int main()
{
    string name;
    char letter;
    int wrongGuesses = 0;
    string word;
    srand((unsigned int)time(NULL)); // Used in the code once to randomize the words in each setting
    
    cout << "+-----------------------------------------------------------------+\n";
    cout << "|                     Hi! Welcome to Hangman!                     |\n"; // Welcomes the user
    cout << "|                                                                 |\n";
    cout << "| Before we start the game, please follow these rules accordingly |\n";
    cout << "|                                                                 |\n";
    cout << "| 1. Please make your guess one letter at a time                  |\n";
    cout << "| 2. Please type in all lower case letters                        |\n";
    cout << "| 3. You have 9 attempts to correctly guess the word              |\n";
    cout << "| 4. The levels are as follows: easy, medium, and hard            |\n";
    cout << "| 5. Please begin by entering the level difficulty you            |\n";
    cout << "|    wish to play as seen above                                   |\n";
    cout << "| 6. Do NOT repeat letters, this will result in a wrong guess     |\n";
    cout << "| 7. HAVE FUN AND ENJOY!                                          |\n";
    cout << "+-----------------------------------------------------------------+\n" << "\n"; // These are the rules of the game
    string level;
    cout << "\nChoose a LEVEL (easy, medium, hard):\n" << endl; // Ask the user for the level they wish to play: easy, medium, or hard
    cin >> level;
    //  Level options
    if (level == "easy" || level == "Easy" || level == "EASY")
    {
        string easy[] = { "blue", "mouse", "home", "bear", "ant", "soccer", "mirror", "key", "tree", "bike", "ball", "glasses", "street", "bottle", "rain", "paper", "people", "needle", "chair", "woods"}; // Use an array to store the easy words, more can be added
        string word;
        
        int n = rand() % 20; // Randomize the 20 easy words from the array each time the user plays
        word = easy[n];
        
        string unknown(word.length(), '_'); // Calls the function for guessing game
                                            // Replace the letters in the word with the _ character
        cout << "\n+-----------------------------------------------+\n";
        cout << "| You chose easy! Have fun!                     |\n";
        cout << "|                                               |\n";
        cout << "| Each letter is represented by a space.        |\n";
        cout << "|                                               |\n";
        cout << "| You have to type only one letter at a time.   |\n";
        cout << "|                                               |\n";
        cout << "| You have " << maxTries << " attempts to try and guess the word.|\n";
        cout << "+-----------------------------------------------+";
        while (wrongGuesses < maxTries) // Loops until all 9 wrong guesses are used
        {
            cout << "\n\n" << unknown;
            cout << "\n\nGuess a letter: ";
            cin >> letter;
            cout << "\n";
            if (letterFill(letter, word, unknown) == 0) // Fill the secret letter if the guess is correct, otherwise increment the number of wrong guesses
            {
                if (wrongGuesses == 0){ // Builds the hangman for each wrong guess the user makes
                    cout << "|==| " << endl;
                    cout << "|    " << endl;
                    cout << "|    " << endl;
                    cout << "|    " << endl;
                    cout << "|    " << endl;
                    cout << "|    " << endl;
                    cout << "^    " << endl;}
                if (wrongGuesses == 1){
                    cout << "|==| " << endl;
                    cout << "|  | " << endl;
                    cout << "|    " << endl;
                    cout << "|    " << endl;
                    cout << "|    " << endl;
                    cout << "|    " << endl;
                    cout << "^    " << endl;}
                if (wrongGuesses == 2){
                    cout << "|==| " << endl;
                    cout << "|  | " << endl;
                    cout << "|  O " << endl;
                    cout << "|    " << endl;
                    cout << "|    " << endl;
                    cout << "|    " << endl;
                    cout << "^    " << endl;}
                if (wrongGuesses == 3){
                    cout << "|==| " << endl;
                    cout << "|  | " << endl;
                    cout << "|  O " << endl;
                    cout << "|  | " << endl;
                    cout << "|    " << endl;
                    cout << "|    " << endl;
                    cout << "^    " << endl;}
                if (wrongGuesses == 4){
                    cout << "|==| " << endl;
                    cout << "|  | " << endl;
                    cout << "|  O " << endl;
                    cout << "| /| " << endl;
                    cout << "|    " << endl;
                    cout << "|    " << endl;
                    cout << "^    " << endl;}
                if (wrongGuesses == 5){
                    cout << "|==| " << endl;
                    cout << "|  | " << endl;
                    cout << "|  O " << endl;
                    cout << "| /|\\" << endl;
                    cout << "|    " << endl;
                    cout << "|    " << endl;
                    cout << "^    " << endl;}
                if (wrongGuesses == 6){
                    cout << "|==| " << endl;
                    cout << "|  | " << endl;
                    cout << "|  O " << endl;
                    cout << "| /|\\" << endl;
                    cout << "|  | " << endl;
                    cout << "|    " << endl;
                    cout << "^    " << endl;}
                if (wrongGuesses == 7){
                    cout << "|==| " << endl;
                    cout << "|  | " << endl;
                    cout << "|  O " << endl;
                    cout << "| /|\\" << endl;
                    cout << "|  | " << endl;
                    cout << "| /  " << endl;
                    cout << "^    " << endl;}
                if (wrongGuesses == 8){
                    cout << "|==| " << endl;
                    cout << "|  | " << endl;
                    cout << "|  O " << endl;
                    cout << "| /|\\" << endl;
                    cout << "|  | " << endl;
                    cout << "| / \\" << endl;
                    cout << "^    " << endl;}
                
                cout << endl << "Whoops! That letter isn't in there!" << endl;
                wrongGuesses++;} // Increments wrong guesses
            else
                {
                    cout << "You guessed a letter! " << endl;
                }
            cout << "You have " << maxTries - wrongGuesses << " guesses left." << endl; // Displays how many guesses the user has left
            if (word == unknown){ // Checks to see if the user guessed the correct word
                cout << "\nYou got it!\n";
                cout << "The word was " << word;
                break;}
        }
        if (wrongGuesses == maxTries) // The user loses if the number of wrong guesses equals their max tries
        {
            cout << "\nSorry, you lose...you have been hung." << endl;
            cout << "The word was: " << word << endl; // Displays the correct word
        }
        cin.ignore();
        cin.get();
        return 0;
    }
    
    else if (level == "medium" || level == "Medium" || level == "MEDIUM")
    {
        string medium[] = { "giraffe", "stretch", "equation", "backpack", "brush", "comfortable", "necklace", "computer", "purple", "community", "recliner", "forest", "sunglasses", "kitchen", "grandfather", "office", "stapler", "shoelace", "squirrel", "apartment"}; // Use an array to store the medium words, more can be added
        
        int n = rand() % 20; // Randomize the 20 easy words from the arrayceach time the user plays
        word = medium[n];
        
        string unknown(word.length(), '_'); // Calls the function for guessing game
                                            // Replace the letters in the word with the _ character
        cout << "\n+-----------------------------------------------+\n";
        cout << "| You chose medium! You can do it!              |\n";
        cout << "|                                               |\n";
        cout << "| Each letter is represented by a space.        |\n";
        cout << "|                                               |\n";
        cout << "| You have to type only one letter at a time.   |\n";
        cout << "|                                               |\n";
        cout << "| You have " << maxTries << " attempts to try and guess the word.|\n";
        cout << "+-----------------------------------------------+";
        while (wrongGuesses < maxTries) // Loops until all 9 wrong guesses are used
        {
            cout << "\n\n" << unknown;
            cout << "\n\nGuess a letter: ";
            cin >> letter;
            cout << "\n";
            if (letterFill(letter, word, unknown) == 0) // Fill the secret letter if the guess is correct, otherwise increment the number of wrong guesses
            {
                if (wrongGuesses == 0){ // Builds the hangman for each wrong guess the user makes
                    cout << "|==| " << endl;
                    cout << "|    " << endl;
                    cout << "|    " << endl;
                    cout << "|    " << endl;
                    cout << "|    " << endl;
                    cout << "|    " << endl;
                    cout << "^    " << endl;}
                if (wrongGuesses == 1){
                    cout << "|==| " << endl;
                    cout << "|  | " << endl;
                    cout << "|    " << endl;
                    cout << "|    " << endl;
                    cout << "|    " << endl;
                    cout << "|    " << endl;
                    cout << "^    " << endl;}
                if (wrongGuesses == 2){
                    cout << "|==| " << endl;
                    cout << "|  | " << endl;
                    cout << "|  O " << endl;
                    cout << "|    " << endl;
                    cout << "|    " << endl;
                    cout << "|    " << endl;
                    cout << "^    " << endl;}
                if (wrongGuesses == 3){
                    cout << "|==| " << endl;
                    cout << "|  | " << endl;
                    cout << "|  O " << endl;
                    cout << "|  | " << endl;
                    cout << "|    " << endl;
                    cout << "|    " << endl;
                    cout << "^    " << endl;}
                if (wrongGuesses == 4){
                    cout << "|==| " << endl;
                    cout << "|  | " << endl;
                    cout << "|  O " << endl;
                    cout << "| /| " << endl;
                    cout << "|    " << endl;
                    cout << "|    " << endl;
                    cout << "^    " << endl;}
                if (wrongGuesses == 5){
                    cout << "|==| " << endl;
                    cout << "|  | " << endl;
                    cout << "|  O " << endl;
                    cout << "| /|\\" << endl;
                    cout << "|    " << endl;
                    cout << "|    " << endl;
                    cout << "^    " << endl;}
                if (wrongGuesses == 6){
                    cout << "|==| " << endl;
                    cout << "|  | " << endl;
                    cout << "|  O " << endl;
                    cout << "| /|\\" << endl;
                    cout << "|  | " << endl;
                    cout << "|    " << endl;
                    cout << "^    " << endl;}
                if (wrongGuesses == 7){
                    cout << "|==| " << endl;
                    cout << "|  | " << endl;
                    cout << "|  O " << endl;
                    cout << "| /|\\" << endl;
                    cout << "|  | " << endl;
                    cout << "| /  " << endl;
                    cout << "^    " << endl;}
                if (wrongGuesses == 8){
                    cout << "|==| " << endl;
                    cout << "|  | " << endl;
                    cout << "|  O " << endl;
                    cout << "| /|\\" << endl;
                    cout << "|  | " << endl;
                    cout << "| / \\" << endl;
                    cout << "^    " << endl;}
                
                cout << endl << "Whoops! That letter isn't in there!" << endl;
                wrongGuesses++; // Increments wrong guesses
            }
            else
            {
                cout << endl << "You guessed a letter!" << endl;
            }
            cout << "You have " << maxTries - wrongGuesses << " guesses left." << endl; // Displays how many guesses the user has left
            if (word == unknown) // Checks to see if the user guessed the correct word
            {
                cout << "\nYou got it!\n";
                cout << "The word was " << word; // Displays the correct word
                break;
            }
        }
        if (wrongGuesses == maxTries) // The user loses if the number of wrong guesses equals their max tries
        {
            cout << "\nSorry, you lose...you have been hung." << endl;
            cout << "The word was: " << word << endl;
        }
        cin.ignore();
        cin.get();
        return 0;
    }
    
    else if (level == "hard" || level == "Hard" || level == "HARD")
    {
        string hard[] = { "phlegm", "gnat", "platypus", "plantation", "rendezvous", "discombobulated", "croquet", "haphazard", "kayak", "oxygen", "zealous", "yacht", "extinguisher", "bagpipes", "dwarves", "haiku", "rogue", "compartment", "psychology", "onomatopoeia"}; // Use an array to store the hard words, more can be added
        
        int n = rand() % 20; // Randomize the 20 easy words from the array each time the user plays
        word = hard[n];
        
        string unknown(word.length(), '_'); // Calls the function for guessing game
                                            // Replace the letters in the word with the _ character
        cout << "\n+-------------------------------------------------+\n";
        cout << "| You chose hard! Hope you are up for a challenge!|\n";
        cout << "|                                                 |\n";
        cout << "| Each letter is represented by a space.          |\n";
        cout << "|                                                 |\n";
        cout << "| You have to type only one letter at a time.     |\n";
        cout << "|                                                 |\n";
        cout << "| You have " << maxTries << " attempts to try and guess the word.  |\n";
        cout << "+-------------------------------------------------+";
        while (wrongGuesses < maxTries) // Loops until all 9 wrong guesses are used
        {
            cout << "\n\n" << unknown;
            cout << "\n\nGuess a letter: ";
            cin >> letter;
            cout << "\n";
            if (letterFill(letter, word, unknown) == 0) // Fill the secret letter if the guess is correct, otherwise increment the number of wrong guesses
            {
                if (wrongGuesses == 0){ // Builds the hangman for each wrong guess the user makes
                    cout << "|==| " << endl;
                    cout << "|    " << endl;
                    cout << "|    " << endl;
                    cout << "|    " << endl;
                    cout << "|    " << endl;
                    cout << "|    " << endl;
                    cout << "^    " << endl;}
                if (wrongGuesses == 1){
                    cout << "|==| " << endl;
                    cout << "|  | " << endl;
                    cout << "|    " << endl;
                    cout << "|    " << endl;
                    cout << "|    " << endl;
                    cout << "|    " << endl;
                    cout << "^    " << endl;}
                if (wrongGuesses == 2){
                    cout << "|==| " << endl;
                    cout << "|  | " << endl;
                    cout << "|  O " << endl;
                    cout << "|    " << endl;
                    cout << "|    " << endl;
                    cout << "|    " << endl;
                    cout << "^    " << endl;}
                if (wrongGuesses == 3){
                    cout << "|==| " << endl;
                    cout << "|  | " << endl;
                    cout << "|  O " << endl;
                    cout << "|  | " << endl;
                    cout << "|    " << endl;
                    cout << "|    " << endl;
                    cout << "^    " << endl;}
                if (wrongGuesses == 4){
                    cout << "|==| " << endl;
                    cout << "|  | " << endl;
                    cout << "|  O " << endl;
                    cout << "| /| " << endl;
                    cout << "|    " << endl;
                    cout << "|    " << endl;
                    cout << "^    " << endl;}
                if (wrongGuesses == 5){
                    cout << "|==| " << endl;
                    cout << "|  | " << endl;
                    cout << "|  O " << endl;
                    cout << "| /|\\" << endl;
                    cout << "|    " << endl;
                    cout << "|    " << endl;
                    cout << "^    " << endl;}
                if (wrongGuesses == 6){
                    cout << "|==| " << endl;
                    cout << "|  | " << endl;
                    cout << "|  O " << endl;
                    cout << "| /|\\" << endl;
                    cout << "|  | " << endl;
                    cout << "|    " << endl;
                    cout << "^    " << endl;}
                if (wrongGuesses == 7){
                    cout << "|==| " << endl;
                    cout << "|  | " << endl;
                    cout << "|  O " << endl;
                    cout << "| /|\\" << endl;
                    cout << "|  | " << endl;
                    cout << "| /  " << endl;
                    cout << "^    " << endl;}
                if (wrongGuesses == 8){
                    cout << "|==| " << endl;
                    cout << "|  | " << endl;
                    cout << "|  O " << endl;
                    cout << "| /|\\" << endl;
                    cout << "|  | " << endl;
                    cout << "| / \\" << endl;
                    cout << "^    " << endl;}
                
                cout << endl << "Whoops! That letter isn't in there!" << endl;
                wrongGuesses++; // Increments wrong guesses
            }
            else
            {
                cout << endl << "You guessed a letter!" << endl;
            }
            cout << "You have " << maxTries - wrongGuesses << " guesses left." << endl; // Displays how many guesses the user has left
            if (word == unknown) // Checks to see if the user guessed the correct word
            {
                cout << "\nYou got it!\n";
                cout << "The word was " << word;
                break;
            }
        }
        if (wrongGuesses == maxTries) // The user loses if the number of wrong guesses equals their max tries
        {
            cout << "\nSorry, you lose...you have been hung." << endl;
            cout << "The word was: " << word << endl; // Displays the correct word
        }
        cin.ignore();
        cin.get();
        return 0;
    }
    
}

int letterFill(char guess, string secretword, string &guessword) // Function for the matches
{
    int i;
    int matches = 0;
    int64_t len = secretword.length();
    for (i = 0; i< len; i++)
    {
        if (guess == guessword[i]) // Did we match this letter previously?
            return 0;
        if (guess == secretword[i]) // Asks if the guess is in the secret word
        {
            guessword[i] = guess;
            matches++;
        }
    }
    return matches;
}

