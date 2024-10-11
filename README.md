# JustCoding
def print_board(board):
    for row in board:
        print(" | ".join(row))
        print("-" * 5)

def check_winner(board, player):
    # Check rows, columns and diagonals
    for row in board:
        if all([cell == player for cell in row]):
            return True
    for col in range(3):
        if all([board[row][col] == player for row in range(3)]):
            return True
    if all([board[i][i] == player for i in range(3)]) or all([board[i][2-i] == player for i in range(3)]):
        return True
    return False

def tic_tac_toe():
    board = [[" " for _ in range(3)] for _ in range(3)]
    players = ["X", "O"]
    turn = 0

    for _ in range(9):  # Maximum 9 moves
        print_board(board)
        row = int(input(f"Player {players[turn]}, enter the row (0, 1, 2): "))
        col = int(input(f"Player {players[turn]}, enter the column (0, 1, 2): "))

        if board[row][col] == " ":
            board[row][col] = players[turn]
            if check_winner(board, players[turn]):
                print_board(board)
                print(f"Player {players[turn]} wins!")
                return
            turn = 1 - turn  # Switch player
        else:
            print("Cell already taken, try again.")

    print_board(board)
    print("It's a tie!")

tic_tac_toe()