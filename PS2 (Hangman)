
# Problem Set 2, hangman.py
# Name: 
# Collaborators:
# Time spent:

# Hangman Game
# -----------------------------------
# Helper code
# You don't need to understand this helper code,
# but you will have to know how to use the functions
# (so be sure to read the docstrings!)
# this is the answer https://pastebin.com/ykuHbfUp
import random
import string

WORDLIST_FILENAME = "words.txt"


def load_words():
    """
    Returns a list of valid words. Words are strings of lowercase letters.
    
    Depending on the size of the word list, this function may
    take a while to finish.
    """
    print("Loading word list from file...")
    # inFile: file
    inFile = open(WORDLIST_FILENAME, 'r')
    # line: string
    line = inFile.readline()
    # wordlist: list of strings
    wordlist = line.split()
    print("  ", len(wordlist), "words loaded.")
    return wordlist



def choose_word(wordlist):
    """
    wordlist (list): list of words (strings)
    
    Returns a word from wordlist at random
    """
    return random.choice(wordlist)

# end of helper code

# -----------------------------------

# Load the list of words into the variable wordlist
# so that it can be accessed from anywhere in the program
wordlist = load_words()

secret_word = "horse"
def is_word_guessed(secret_word, letters_guessed):
    '''
    secret_word: string, the word the user is guessing; assumes all letters are
      lowercase
    letters_guessed: list (of letters), which letters have been guessed so far;
      assumes that all letters are lowercase
    returns: boolean, True if all the letters of secret_word are in letters_guessed;
      False otherwise
    '''
    
    for i in secret_word:
        if i not in letters_guessed:
            return False
    return True

def get_guessed_word(secret_word, letters_guessed):
    '''
    secret_word: string, the word the user is guessing
    letters_guessed: list (of letters), which letters have been guessed so far
    returns: string, comprised of letters, underscores (_), and spaces that represents
      which letters in secret_word have been guessed so far.
    '''
    string=" "
    for letter in secret_word:
        if letter in letters_guessed:
            string+=letter+" "
        else:
            string+="_ "
    return string


def get_available_letters(letters_guessed):
    '''
    letters_guessed: list (of letters), which letters have been guessed so far
    returns: string (of letters), comprised of letters that represents which letters have not
      yet been guessed.
    '''
    import string
    
    letters_left=string.ascii_lowercase
    for letter in letters_guessed:
        letters_left=letters_left.replace(letter,"")
    print("Available letters: ")
    return letters_left



def hangman(secret_word):
    '''
    secret_word: string, the secret word to guess.
    
    Starts up an interactive game of Hangman.
    
    * At the start of the game, let the user know how many 
      letters the secret_word contains and how many guesses s/he starts with.
      
    * The user should start with 6 guesses

    * Before each round, you should display to the user how many guesses
      s/he has left and the letters that the user has not yet guessed.
    
    * Ask the user to supply one guess per round. Remember to make
      sure that the user puts in a letter!
    
    * The user should receive feedback immediately after each guess 
      about whether their guess appears in the computer's word.

    * After each guess, you should display to the user the 
      partially guessed word so far.
    
    Follows the other limitations detailed in the problem write-up.
    '''
    print("Welcome to the game hangman!")
    print("I'm thinking of a word that is",len(secret_word),"letters long.")
    print("You have 10 guesses. Your guess has to be an alphabet.")
    print("---------------")
    
    guesses_remaining=11
    letters_guessed=[]
    warnings=3
    vowel_list=['a','e','i','o','u']
    while guesses_remaining>1 and not is_word_guessed(secret_word, letters_guessed):
        guesses_remaining-=1
        print("You have",guesses_remaining,"guesses left.")
        print(get_available_letters(letters_guessed))
        guess_a_letter=input("Please guess a letter: ")
            
        
        if str.isalpha(guess_a_letter):
            if guess_a_letter in secret_word:
                if guess_a_letter not in letters_guessed:
                    letters_guessed.append(guess_a_letter)
                    print("Good guess!:",get_guessed_word(secret_word, letters_guessed))
                else:
                    print("Oops! You've already guessed that letter: ",get_guessed_word(secret_word, letters_guessed))   
                    if warnings>1:
                        warnings-=1
                        print("You have",warnings,"warnings left.")
                    else:
                        guesses_remaining-=1 
                        print("You have used up all your warnings. Your penalty is 1 guess.")
            else:
                 if guess_a_letter not in letters_guessed:
                     if guess_a_letter in vowel_list:
                         letters_guessed.append(guess_a_letter)
                         guesses_remaining-=1
                         print("Oops! That letter isn't in my word:",get_guessed_word(secret_word, letters_guessed))
                     else:
                         letters_guessed.append(guess_a_letter)
                         print("Oops! That letter isn't in my word:",get_guessed_word(secret_word, letters_guessed))
                 else:
                     print("Oops! You've already guessed that letter: ",get_guessed_word(secret_word, letters_guessed))
                     if warnings>1:
                         warnings-=1
                         print("You have",warnings,"warnings left.")
                     else:
                         guesses_remaining=-1
                         print("You have used up all your warnings. Your penalty is 1 guess.")
    
        else:
            print("Oops! That isn't a valid letter: ",get_guessed_word(secret_word, letters_guessed))
            if warnings>1:
                warnings-=1
                print("You have",warnings,"warnings left.")
            else:
                guesses_remaining-=1 
                print("You have used up all your warnings. Your penalty is 1 guess.")
    
        print("--------------------------------")
    
    if is_word_guessed(secret_word, letters_guessed):
        print("Congratulations, you won!")
        unique=[]
        for i in secret_word:
            if i not in unique:
                unique.append(i)
        total_score = guesses_remaining*len(unique)
        print("Your score is",total_score,"!")
        
    if not is_word_guessed(secret_word, letters_guessed) and guesses_remaining==0:
        print("I'm sorry, you lost. The secret word is",secret_word,".")

# When you've completed your hangman function, scroll down to the bottom
# of the file and uncomment the first two lines to test
#(hint: you might want to pick your own
# secret_word while you're doing your own testing)


# -----------------------------------



#def match_with_gaps(my_word, other_word):
    '''
    my_word: string with _ characters, current guess of secret word
    other_word: string, regular English word
    returns: boolean, True if all the actual letters of my_word match the 
        corresponding letters of other_word, or the letter is the special symbol
        _ , and my_word and other_word are of the same length;
        False otherwise: 
    '''
    # FILL IN YOUR CODE HERE AND DELETE "pass"
    #pass



#def show_possible_matches(my_word):
    '''
    my_word: string with _ characters, current guess of secret word
    returns: nothing, but should print out every word in wordlist that matches my_word
             Keep in mind that in hangman when a letter is guessed, all the positions
             at which that letter occurs in the secret word are revealed.
             Therefore, the hidden letter(_ ) cannot be one of the letters in the word
             that has already been revealed.

    '''
    # FILL IN YOUR CODE HERE AND DELETE "pass"
    #pass



#def hangman_with_hints(secret_word):
    '''
    secret_word: string, the secret word to guess.
    
    Starts up an interactive game of Hangman.
    
    * At the start of the game, let the user know how many 
      letters the secret_word contains and how many guesses s/he starts with.
      
    * The user should start with 6 guesses
    
    * Before each round, you should display to the user how many guesses
      s/he has left and the letters that the user has not yet guessed.
    
    * Ask the user to supply one guess per round. Make sure to check that the user guesses a letter
      
    * The user should receive feedback immediately after each guess 
      about whether their guess appears in the computer's word.

    * After each guess, you should display to the user the 
      partially guessed word so far.
      
    * If the guess is the symbol *, print out all words in wordlist that
      matches the current guessed word. 
    
    Follows the other limitations detailed in the problem write-up.
    '''
    # FILL IN YOUR CODE HERE AND DELETE "pass"
    #pass



# When you've completed your hangman_with_hint function, comment the two similar
# lines above that were used to run the hangman function, and then uncomment
# these two lines and run this file to test!
# Hint: You might want to pick your own secret_word while you're testing.


#if __name__ == "__main__":
    # pass

    # To test part 2, comment out the pass line above and
    # uncomment the following two lines.
    
    #secret_word = choose_word(wordlist)
    #hangman(secret_word)

###############
    
    # To test part 3 re-comment out the above lines and 
    # uncomment the following two lines. 
    
    
    #hangman_with_hints(secret_word)
