from random import randrange
from string import *


WORDLIST_FILENAME = "HangmanGame_word.txt"

def load_words():
    print ("Loading word list from file...")
    inFile = open(WORDLIST_FILENAME, 'r')
    line = inFile.readline() 
    wordlist = line.split(" ")
    print ("  ", len(wordlist), "words loaded.")
    print ('Enter play_hangman() to play a game of hangman!')
    return wordlist

words_dict = load_words()

def get_word():
    """ Returns a random word from the word list """
    word = words_dict[randrange(0, len(words_dict))]
    return word

MAX_GUESSES = 6


secret_word = 'claptrap' 
letters_guessed = []

def word_guessed():
   
    global secret_word
    global letters_guessed

    return all(letter in letters_guessed for letter in secret_word)

def print_guessed():
  
    global secret_word
    global letters_guessed
    
    displayed_word = ''.join(letter if letter in letters_guessed else '_' for letter in secret_word)
    print("Current word: ", displayed_word)

def play_hangman():
    global secret_word
    global letters_guessed
    mistakes_made = 0


    secret_word = get_word()
    letters_guessed = []

    print("Welcome to Hangman!")
    
    while mistakes_made < MAX_GUESSES:
        print_guessed()
        print(f"Guesses remaining: {MAX_GUESSES - mistakes_made}")
        guess = input("Please guess a letter: ").lower()

        if guess in letters_guessed:
            print("You've already guessed that letter. Try again.")
            continue
        elif len(guess) != 1 or not guess.isalpha():
            print("Invalid input. Please guess a single letter.")
            continue
        
        letters_guessed.append(guess)

        if guess in secret_word:
            print("Good guess!")
        else:
            mistakes_made += 1
            print("Oops! That letter is not in the word.")
        
        if word_guessed():
            print_guessed()
            print("Congratulations! You've guessed the word:", secret_word)
            break
    else:
        print("Sorry, you've run out of guesses. The word was:", secret_word)
