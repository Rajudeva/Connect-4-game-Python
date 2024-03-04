# Connect-4-game-Python
board = [] # List for holding the board

for x in range(6):
    board.append(["O"] * 7) # Builds 7 x 6 board (rows x columns)

# Function for printing the board
def print_board(board):  
    for row in board:
        print(" ".join(row))

print('Welcome to Connect Four')

player_one = input('Player 1. Enter your name: ')
player_two = input('Player 2. Enter your name: ') # Gets players names

print('%s vs. %s' % (player_one, player_two))
print('--------------')
print_board(board)
print('Player 1 is Red(R) and Player 2 is Black(B)')
print('Let\'s play!!' ) # Game's 'Opening'

turn = 0 # Keeps track of turn

while True:
    if turn % 2 == 0: # Determines whose turn it is by checking for even or odd turn 
        print('%s. Choose a column to drop your chip' % (player_one))
        choice = int(input('Column: ')) # Determines what column player will drop chip
        player = 'R' # Player 1 is Red
    else:
        print('%s. Choose a column to drop your chip' % (player_two))
        choice = int(input('Column: '))
        player = 'B' # Player 2 is Black

    if 1 <= choice <= 7: # Check if the chosen column is within the bounds
        for row in range(5, -1, -1): # Check from bottom to top for empty slot
            if board[row][choice - 1] == 'O':
                board[row][choice - 1] = player
                break
        else:
            print("Column is full!!")
            continue
    else:
        print("Invalid column number!")
        continue

    print_board(board)
    turn += 1

    # Check for win conditions or draw here
    # You need to implement this part

    if turn == 6:
        print('Game Over man!')
        break
