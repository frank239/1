from random import randint

board = []

num_boat = randint(1,4)
if num_boat == 1:
    for x in range(5):
        board.append(["O"] * 5) #Crée mon board
if num_boat == 2:
    for x in range(6):
        board.append(["O"] * 6) #Crée mon board
if num_boat == 3:
    for x in range(7):
        board.append(["O"] * 7) #Crée mon board
if num_boat == 4:
    for x in range(8):
        board.append(["O"] * 8) #Crée mon board

def print_board(board): #Permet de pas tout soit collé
    for row in board:
        print " ".join(row)
def print_num(num):
    print "There is " + num_boat + "hidden boats"
print "Let's play Battleship!" #Début de partie
print_num(num_boat)
print_board(board)

def random_row(board): #Défini le rang du bateau
    return randint(0, len(board[0]) - 1)

def random_col(board): #Défini la colone du bateau
    return randint(0, len(board[0]) - 1)

ship_row = random_row(board)
ship_col = random_col(board)

# Everything from here on should go in your for loop!
# Be sure to indent four spaces!
for turn in range(4): #Permet 4 Guess
    print "Turn", turn + 1
    guess_row = int(raw_input("Guess Row:"))
    guess_col = int(raw_input("Guess Col:"))

    if guess_row == ship_row and guess_col == ship_col:
        print "Congratulations! You sunk my battleship!"
        break
    else:
        if (guess_row < 0 or guess_row > 4) or (guess_col < 0 or guess_col > 4):
            print "Oops, that's not even in the ocean."
        elif(board[guess_row][guess_col] == "X"):
            print "You guessed that one already."
        else:
            print "You missed my battleship!"
            board[guess_row][guess_col] = "X"
    # Print (turn + 1) here!
        print_board(board)
        if turn == 3:
            print "Game Over"
