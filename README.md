# Python-Milestone-project-1
from IPython.display import clear_output

#prints board
def display_board(board):
    print(test_board[1]+'|'+test_board[2]+'|'+test_board[3])
    print(test_board[4]+'|'+test_board[5]+'|'+test_board[6])
    print(test_board[7]+'|'+test_board[8]+'|'+test_board[9])
    pass


 
#takes in player input 
    def player_input():
    
    marker = ''
    while marker != 'X' and marker != 'O':
        marker = input('Player1, please pick X or O: ')
    player1 = marker
    
    if player1 == 'X':
        player2 = 'O'
    else:
        player2 = 'X'
    return (player1,player2)
    
    def place_marker(board, marker, position):
    board[position] = marker
    pass
    
    #function that takes in a board and mark and checks to see if it has won
    
    def win_check(board, mark):
    return ((board[1] == mark and board[2] == mark and board [3] == mark) or #row check
    (board[4] == mark and board[5] == mark and board [6] == mark) or
    (board[7] == mark and board[8] == mark and board [9] == mark) or
    (board[2] == board[5] == board[8] == mark) or #column check
    (board[3] == board[6] == board[9] == mark) or
    (board[1] == board[4] == board[7] == mark) or
    (board[1] == board[5] == board[9] == mark) or #diagonal check
    (board[3] == board[5] == board[7] == mark))    
    
    # checks if board is full
    def space_check(board, position):
       
    return board[position] == ' '
    
