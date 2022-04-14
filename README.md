# Python-Milestone-project-1
from IPython.display import clear_output

#prints board
from IPython.display import clear_output

def display_board(board):
    clear_output()
    print('  |   |')
    print('' + board[7] + ' | ' + board[8] + ' | ' + board[9])
    print('  |   |')
    print('-----------')
    print('  |   |')
    print('' + board[4] + ' | ' + board[5] + ' | ' + board[6])
    print('  |   |')
    print('-----------')
    print('  |   |')
    print('' + board[1] + ' | ' + board[2] + ' | ' + board[3])
    print('  |   |')
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
    
    # checks if board space is free
    def space_check(board, position):
       
    return board[position] == ' '
    
    # check if board space is full
    def full_board_check(board):
    
    for i in range(1,10):
        if space_check(board,i):
            return False
        
    # board is full if we return true
    return True
    
    # asks for a player's position and checks if it's free
    def player_choice(board):
    
    position = 0
    
    while position not in [1,2,3,4,5,6,7,8,9] or not space_check(board,position):
        position = int(input('Choose a position: (1-9)'))
    
    return position
    
    #asks a player if they want to play again and returns a boolean
    def replay():
    
    choice = input("Play again? Enter yes or No")
    
    return choice == 'Yes'
    
    #While loop to keep the game running
print('Welcome to Tic Tac Toe!')

while True:
    # PLAY THE GAME
    
    # Set the game up here
    the_board = [' ']*10
    player1_marker,player2_marker = player_input()
    
    turn = choose_first()
    print(turn + ' will go first')
    
    play_game = input('Ready to play? y or n? ')
    
    if play_game == 'y':
        game_on = True
    else:
        game_on = False
    while game_on:
        
        if turn == 'Player 1':
            
            # Show the board
            display_board(the_board)
            # Choose a position
            position = player_choice(the_board)
            # Place the marker on the position
            place_marker(the_board,player1_marker,position)
            # Check if they won
            if win_check(the_board,player1_marker):
                display_board(the_board)
                print('PLAYER 1 HAS WON!!')
                game_on = False
            else:
                if full_board_check(the_board):
                    display_board()
                    print("TIE GAME!")
                    break
                else:
                    turn = 'Player 2'
                

        else: 
            # Show the board
            display_board(the_board)
            # Choose a position
            position = player_choice(the_board)
            # Place the marker on the position
            place_marker(the_board,player2_marker,position)
            # Check if they won
            if win_check(the_board,player2_marker):
                display_board(the_board)
                print('PLAYER 2 HAS WON!!')
                game_on = False
            else:
                if full_board_check(the_board):
                    display_board()
                    print("TIE GAME!")
                    break
                else:
                    turn = 'Player 1'
      

    if not replay():
        break
    # BREAK OUT OF THE WHILE LOOP ON replay()
   
    
