import random

def choose_word():
    words = ['apple', 'banana', 'cherry', 'orange', 'grape', 'pineapple']
    return random.choice(words)

def display_word(word, guessed_letters):
    display = ""
    for letter in word:
        if letter in guessed_letters:
            display += letter
        else:
            display += "_"
    return display

def hangman():
    word = choose_word()
    guessed_letters = []
    attempts = 6
    
    print("Welcome to Hangman!")
    
    while True:
        print("\nAttempts left:", attempts)
        print("Guessed letters:", guessed_letters)
        print("Word:", display_word(word, guessed_letters))
        
        guess = input("Guess a letter: ").lower()
        
        if guess in guessed_letters:
            print("You already guessed that letter.")
            continue
        
        guessed_letters.append(guess)
        
        if guess not in word:
            attempts -= 1
            print("Incorrect guess!")
            if attempts == 0:
                print("Sorry, you're out of attempts! The word was:", word)
                break
        else:
            print("Correct guess!")
        
        if all(letter in guessed_letters for letter in word):
            print("Congratulations, you've guessed the word:", word)
            break

hangman()
