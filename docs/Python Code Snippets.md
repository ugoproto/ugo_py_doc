---

[TOC]

---

**Foreword**

Code snippets. Python 2.

---

## A Battleship Game

<sub>build, board, grid, row, column, list, assign, random, value, loop, conditional, if, else, elif</sub>

```python
from random import randint

board = []

for x in range(5):
    board.append(["O"] * 5)

def print_board(board):
    
    for row in board:
        print " ".join(row)

print "\nLet's play Battleship! You have 4 strikes to sink by ship.\n"
print_board(board)

def random_row(board):
    
    return randint(0, len(board) - 1)

def random_col(board):
    
    return randint(0, len(board) - 1)

ship_row = random_row(board)
ship_col = random_col(board)
#ship_row = 1 to test and fix to (1,1)
#ship_col = 1

for turn in range(5):
    turn += 1
    if turn == 5:
        print "\nGame Over"
        print "The ship was here => I\n"
        board[ship_row - 1][ship_col - 1] = "I"
        print_board(board)
        break
    else:
        print "\nTurn", turn

        guess_row = int(raw_input("Guess Row (1 to 5): "))
        guess_col = int(raw_input("Guess Col (1 to 5): "))

        if (guess_row == ship_row) and (guess_col == ship_col):
            print "\nCongratulations! You sank my battleship!\n"

            guess_row = guess_row - 1
            guess_col = guess_col - 1
            board[guess_row][guess_col] = "S"

            print_board(board)
            print "\nGame Over"
            break

        elif (guess_row < 1 or guess_row > 5) or (guess_col < 1 or guess_col > 5):
            print "\nOops, that's not even in the ocean.\n"

        elif board[guess_row - 1][guess_col - 1] == "X":
            print "\nYou guessed that one already.\n"
            print_board(board)
            
        else:
            print "\nYou missed my battleship!\n"
            board[guess_row - 1][guess_col - 1] = "X"
            print_board(board)

```

## An Interactive Calendar

<sub>add, delete, update, exit, dictionary, loop, conditional, if, else, elif</sub>

```python
from time import sleep, strftime

his_name = raw_input("What is your first name? ")
his_name = str(his_name)
# calendar will store the dates as keys and the events as values

calendar = {}

def welcome():

    print("Welcome " + his_name +".")

    print("Calendar starting...")
    sleep(0.5)
    print("Today is: " + strftime("%A, %B %d, %Y"))
    print("It is currently: " + strftime("%H:%M:%S"))
    sleep(0.5)

def start_calendar():

    welcome()
    print("What would you like to do?")
    print(calendar)
    start = True
  
    while start:
        user_choice = raw_input("Choose between: 'A' to Add, 'U' to Update, 'V' to View, 'D' to Delete or 'X' to Exit? ").upper()
        
        if user_choice == 'V': # V
            if len(calendar.keys()) < 1:
                print("The calendar is empty")
            else:
                print(calendar)
            
        elif user_choice == 'U': # U
            if len(calendar.keys()) < 1:
                print("The calendar is empty")
            else:
                print(calendar)
                date = raw_input("What date? ")
                update = raw_input("Enter the update: ")
                # could be more control here...
                calendar[date] = update # without checking if the date is valid or if it already exists (which could override things)!
                print("Successful!")
                print(calendar)
          
        elif user_choice == 'A': # A
            event = raw_input("Enter event: ")
            date = raw_input("Enter date (MM/DD/YYYY): ")
            if (len(date) > 10 or int(date[6:]) < int(strftime("%Y"))): # could be more control...
                print("Invalid date format.")
                try_again = raw_input("Try Again? 'Y' for Yes, 'N' for No: ").upper()
                if try_again == 'Y':
                    continue #! break, continue, start is still True
                else:
                    start == False
            else:
                calendar[date] = event # without checking if the date is valid or if it already exists (which could override things)!
                print("Successful!")
                print(calendar)
         
        elif user_choice == 'D': # D
            if len(calendar.keys()) < 1:
                print("The calendar is empty.")
            else:
                print(calendar)
                event = raw_input("What event? ") # could be more option like: What date?
                for date in calendar.keys():
                    if event == calendar[date]:
                        del calendar[date] # del a[], [1], ["a"], [1:3], [5:], [:9], etc.
                        print("Deleted.")
                        print(calendar)
                    else:
                        print("Incorrect.")
            
        elif user_choice == 'X': # X
            start = False
        
        else:
            print("Invalid command.")
            break

start_calendar()
```

## A Gradebook for Students

<sub>students, marks, grades, compute, average, weighted</sub>

First, create 3 dictionaries.

Second, add names, marks.

```python
lloyd = {
    "name" : "Lloyd",
    "homework" : [90.0, 97.0, 75.0, 92.0],
    "quizzes" : [88.0, 40.0, 94.0],
    "tests" : [75.0, 90.0]
}

alice = {
    "name": "Alice",
    "homework" : [100.0, 92.0, 98.0, 100.0],
    "quizzes" : [82.0, 83.0, 91.0],
    "tests" : [89.0, 97.0]
}

tyler = {
    "name" : "Tyler",
    "homework" : [0.0, 87.0, 75.0, 22.0],
    "quizzes" : [0.0, 75.0, 78.0],
    "tests" : [100.0, 100.0]
}
```

Third, make a list.

```python
students= [lloyd, alice, tyler]

cases = ["homework", "quizzes", "tests"]

w_calc = [0.10, 0.30, 0.60]

all_average = 0.0
```

Print out.


```python
print "\nStudents' Grades".upper()

print ""

for student in students:
    print student["name"].upper()
    print "Homework"
    print student["homework"]
    print "Quizzes"
    print student["quizzes"]
    print "Tests"
    print student["tests"]
    print ""
```

Compute averages.

```python
def average(numbers):
    
    total = sum(numbers)
    temp = float(total) / len(numbers)
    return temp

print "Students' Averages".upper()

print ""

for c in cases:
    cc = c.upper()
    print cc
    for student in students:
        numbers = student[c]
        calc = round(average(numbers),1)
        print student["name"]
        print calc
    print ""
```

Compute weighted averages.


```python
def w_average(marks):
    
    #w_calc = [0.10, 0.30, 0.60]
    s_calc = 0
    w = 0
    while w < len(w_calc):
        s_calc += w_calc[w] * marks[w]
        w += 1
    return s_calc

def get_letter_grade(score):
    
    if score >= 90:
        return "A"
    elif score >= 80:
        return "B"
    elif score >= 70:
        return "C"
    elif score >= 60:
        return "D"
    else:
        return "F"

def get_class_average(ind):
    class_total = round(ind / len(students), 1)
    return class_total

print "Students' Weighted Average".upper()

print " Ponderation [Homeworks, Quizzes, Tests]: ["+str(float(w_calc[0])*100)+", "+str(float(w_calc[1])*100)+", "+str(float(w_calc[2])*100)+"]"

print ""

for student in students:
    print(student["name"] + "'s marks are:").upper()
    l_calc = []
    for c in cases:    
        numbers = student[c]
        calc = round(average(numbers),1)
        l_calc.append(calc)
    print l_calc
    print("For a weighted average of:")
    ind_average = round(w_average(l_calc),1)
    print ind_average
    print("Standing for a:")
    print get_letter_grade(ind_average)
    all_average += ind_average
    print ""

print("Finally, The class average is:").upper()
print get_class_average(all_average)
```

## Guess Games

<sub>random, generate, number, conditional, if, else, ifel, loop</sub>

Guess a number.

```python
import random

print "Lucky Numbers! 3 numbers will be generated."
print "If one of them is a '5', you lose!"

count = 0

while count < 3:
    num = random.randint(1, 6)
    print num
    if num == 5:
        print "Sorry, you lose!"
        break
    count += 1
else:
    print "You win!"
```

Guess a number (more).

```python
from random import randint

# Generates a number from 1 through 10 inclusive
random_number = randint(1, 10)

# print random_number
guesses_left = 3
print "Guess right!"

while guesses_left > 0:
    print "You have "+str(guesses_left)+" attempts."
    guess = raw_input("Guess a number from 1 to 10: ")
    if int(guess) == random_number:
        print "You win!"
        break
    elif guesses_left == 1:
        print "You lose."
        break
    else:
        guesses_left -= 1
        print "Try again."
```

Roll a dice.

```python
from random import randint
from time import sleep

def get_user_guess():
    
    user_guess = int(raw_input("Guess a number: "))
    return user_guess

def roll_dice(number_of_sides):
    
    first_roll = randint(1, number_of_sides)
    second_roll = randint(1, number_of_sides)
    max_value = number_of_sides * 2
    print "The maximum value is: "+str(max_value)
    sleep(1)
    user_guess = get_user_guess()
    if user_guess > max_value:
        print "Your guess is higher than the max allowed ("+str(max_value)+"). Please, take another guess."
        return # exit the if block is condition met
    else:
        print "Rolling..."
        sleep(1)
        print "First roll is: %d" % (first_roll)
        sleep(1)
        print "Second roll is: %d" % (second_roll)
        total_roll = first_roll + second_roll
        print "Result..."
        sleep(1)
        if user_guess > total_roll:
            print "You win since your guess, "+str(user_guess)+", is greater than the total roll, "+str(total_roll)
            return # exit
        else:
            print "You lose!"
            return # exit

roll_dice(6)
```

Rock, paper, Scissors.

```python
from random import randint
from time import sleep

options = ["R", "P", "S"]
LOSE = "You lost!" # constant, uppercase
WIN = "You win!"

def decide_winner(user_choice, computer_choice):
    
    print("You picked: "+str(user_choice))
    print "Computer selecting..."
    
    sleep(1)
    
    print("Computer picks: "+str(computer_choice))
    
    user_choice_index = options.index(user_choice)
    computer_choice_index = options.index(computer_choice) # !!!!!
    
    if user_choice_index == computer_choice_index:
        print "Tie!"
    elif user_choice_index == 0 and computer_choice_index == 2:
        print WIN
    elif user_choice_index == 1 and computer_choice_index == 0:
        print WIN
    elif user_choice_index == 2 and computer_choice_index == 1:
        print WIN
    elif user_choice_index > 2:
        print "Invalid choice!!!"
    else:
        print LOSE

def play_RPS():
    
    print "Let's pay Rock-Paper-Scissors"
    
    user_choice = raw_input("Select R for Rock, P for Paper, or S for Scissors: ")
    
    sleep(1)
    
    user_choice = user_choice.upper()
    # computer_choice = options[randint(0,2)] 
    # pull out an element from a list, the 1st (0) out of 3 (2)
    
    computer_choice = options[randint(0,len(options)-1)] 
    # This will ensure that if we ever add more options to the game, we won't have to change this line of code.
    
    decide_winner(user_choice, computer_choice)

play_RPS()
```

## Regex Tools

Remove vowels

```python
def anti_vowel(text):
    
    vowels = "aAeEiIoOuU"
    for char in text:
        for vow in vowels:
            if vow == char:
                text = text.replace(char,"")
    return text

print anti_vowel("allo")
```

Remove all but punctuation.

```python
def anti_vowel(text):
    
    text = text.lower()
    vowels = "abcdefghijklmnopqrstuvwxyz1234567890$-"
    
    for char in text:
        for vow in vowels:
            if vow == char:
                text = text.replace(char,"")
    for char in text:
        if char == " ":
            text = text.replace(char,"")
    return text

print anti_vowel("The plethora of object oriented approaches leads to a natural question. Which one should you use? With respect to S3 and S4 classes, the S3 class is more flexible, and the S4 class is a more structured approach. This is a nice way of saying that the S3 class approach is for unaware slobs and is a sloppy way to shoot yourself in the foot, while the S4 class is for uptight pedants. Our focus here is on S3 classes. Before we delve into the details of S3 classes we need to talk about memory environments. These can be used to great effect in S3 classes to make your codes totally incomprehensible. On the down side they help give S3 classes their flexibility. An environment can be thought of as a local scope. It has a set of variables associated with it. You can access those variables if you have the \"ID\" associated with the environment. There are a number of commands you can use to manipulate and obtain the pointers to your environments. You can also use the assign and get commands to set and get the values of variables within an environment.")
```

Scrape a text.

<sub>urllib2, scrape, scrapy, parse, parser, split, extract, subset, join, project, gutenberg, split, conditional, count, occurences<sub>

```python
import urllib2

response = urllib2.urlopen('http://gutenberg.org/')

# find Les Miserables by Victor Hugo
# http://www.gutenberg.org/ebooks/135
# the book is available in HTML, epub with images, w/o images, kindle with images, w/o images, and more...

response = urllib2.urlopen('http://www.gutenberg.org/files/135/135-h/135-h.htm')
html = response.read()

print html

sad = 0

list_of_words = html.split(' ')

for word in list_of_words:
    if word == 'sad':
        sad += 1
        
print sad # count occurences
```

Scrabble score.

<sub>dictionary, count, conditonal, if, loop</sub>

```python
score = {"a": 1, "c": 3, "b": 3, "e": 1, "d": 2, "g": 2, 
         "f": 4, "i": 1, "h": 4, "k": 5, "j": 8, "m": 3, 
         "l": 1, "o": 1, "n": 1, "q": 10, "p": 3, "s": 1, 
         "r": 1, "u": 1, "t": 1, "w": 4, "v": 4, "y": 4, 
         "x": 8, "z": 10}

def scrabble_score(word):
    
    word2 = word.lower()
    
    print word2+":",
    points = 0
    for letter in word2:
        if letter == str(letter):
            points += score[letter]
    return points

print scrabble_score("ab")
print scrabble_score("allo")
print scrabble_score("xylophone")
print scrabble_score("coding")
print scrabble_score("yak")
```

## RGB-HEX Converter

<sub>convert, bitwise, hexadecimal, hex, rgb, color</sub>

```python
def rgb_hex():
    
    invalid_msg = "Invalid entry"
    red = int(raw_input("Enter a 'red' (R) value, from 0 to 255: "))
    if red < 0 or red > 255:
        print invalid_msg
        return # return will exit the function, w/o return, the function jumps to the next line...

    green = int(raw_input("Enter a 'green' (G) value, from 0 to 255: "))
    if green < 0 or green > 255:
        print invalid_msg
        return

    blue = int(raw_input("Enter a 'blue' (B) value, from 0 to 255: "))
    if blue < 0 or blue > 255:
        print invalid_msg
        return

    val = red << 16 + green << 8 + blue
    # A hexadecimal number can be represented with 3 bytes, a byte for each part of R, G, and B. A byte is composed of two nibbles (4 bit numbers). Hexadecimal numbers have 6 characters and each nibble represents a hex character.
    # Shifting red to the left by 16 bits will insert 16 bits that will hold the place of green (shifted 8 bits to the left) and blue (no shift).
    # Become familiar with bits by reading more here.
    print "%s" %(hex(val)[2:].upper()) # string formatting

def hex_rgb():
    
    invalid_msg = "Invalid entry"
    hex_val = raw_input("Enter a color (six hexadecimal digits): ")
    if len(hex_val) != 6:
        print "Invalid Entry"
    else:
        hex_val = int(hex_val, 16)
    two_hex_digits = 2 ** 8
    blue = hex_val % two_hex_digits
    hex_val = hex_val >> 8
    green = hex_val % two_hex_digits
    hex_val = hex_val >> 8
    red = hex_val % two_hex_digits
    print "Red: %s Green: %s Blue: %s" %(red, green,blue)

def convert():
    
    while True:
        option = str(raw_input("Enter '1' to convert RGB to HEX. Enter '2' to convert HEX to RGB. Enter 'X' to Exit:. "))
        if option == '1':
            print "RGB to Hex..."
            rgb_hex()
        elif option == '2':
            print "Hex to RGB..."
            hex_rgb()
        elif option == 'X' or option == 'x':
            break
        else:
            print "Error"

convert()
```

## Project DNA Analysis

Given the three suspects' DNA and the sample DNA retrieved from the keyboard, figure out who the spy is!

<sub>list, open, close, file, read, line, loop, conditional, if, match</sub>

```python
sample = ['GTA','GGG','CAC']

def read_dna(dna_file):
    
    dna_data = "" # empty string
    
    with open(dna_file, "r") as f: # f = open(dna_file, "r"); with, as
        for line in f:
            dna_data += line
        return dna_data

def dna_codons(dna):
    
    codons = []
    for i in range(0,len(dna),3): # slice strings of 3 letters
        if i+3 < len(dna): # make sure that you don't add a string to the codon list that isn't at least 3 letters long
            codons.append(dna[i:i+3]) # append to list in appendig positions 0 (new entry), 1, 2, stopping before 3
    return codons

def match_dna(dna):
    
    matches = 0
    for codon in dna:
        if codon in sample: # if ,in
            matches += 1
    return matches

def is_criminal(dna_sample):
    
    dna_data = read_dna(dna_sample)
    codons = dna_codons(dna_data)
    num_matches = match_dna(codons)
    if num_matches >= 3:
        print((dna_sample)[:-4]).upper(),
        print(": number of matches = " + str(num_matches) + "; the investigation will proceed further more with this suspect.")
    else:
        print((dna_sample)[:-4]).upper(),
        print(": no evidence; the suspect can be freed.")

a = "suspect1.txt"
is_criminal(a)

a = "suspect2.txt"
is_criminal(a)

a = "suspect3.txt"
is_criminal(a)
```

suspect1.txt

```text
ATCGAAAGCACAATCATGCATCGTGCCAGTGTGTTCGTGTCATCTAGGACGGGGCCATAGGATATATAATTCAATTAAGAATACCTTATACTACTGTCCCCTGTGGTTCGAAGGGGAACTATTTCGTGGGGCGAGCCCACACCGTCTCTTCTGCGGAAGACTTAACACGTTAGGGAGGTGGAATAGTTTCGAACGATGGTTATTAATCGTGATAACGGAACGCTGTCTGGAGGATGAGTCTGACGGTGTGTGACTCGATCAGTCACTCGCTATTCGAACTGCGCGAAAGATCCCAGCGCT
```

suspect2.txt

```text
CCGTAAGACAAATAATTCAATAAAGATGTCGTTTTGCTAGTTTACGTCAAGGTGTCACGCGCCATCTCTGAGCAGGTGGGCCGACGAGACATTATCCCTGGAGTATCAAACCCGTACAAAGGGAACATCCACACTTTGGTGAATCGAAGCGCGGCATCAGGATTTCCTTTTGGATACCTGAAACAAAGCCCATCGTGGTCCTTAGACTTGGCACACTTACACCTGCAGCGCGCGCATGTGGAATTAGAGGCCAAGTTCGATCCCTACACCGACGTACGATGCAACTGTGTGGATGTGACG
```

suspect3.txt

```text
TCGCATAAGTACAGTAGATCCTCCCCGCGCATCCTATTTATTAAGTTAATTCTACAGCAATACGATCATATGCGGATCCGCAGTGGCCGGTAGACACACCATGCACTTGATTCCGAGGCCTGTCCCGATATATGAACCCAAACTAGAGCGAGGCTGTTGACGTTTGGAGTTGAAAAAATCTATTATACCAATCGGCTTCAACGTGCTCCACGGCAGGCGCCTGACGAGAGGCCCACACCGAGGAAGTAGACTGTTGCACGTTGAGGATAGCGCTAGCTAACAAAGACGCCTGCTACAACA
```
