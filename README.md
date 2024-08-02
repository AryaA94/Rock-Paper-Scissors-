import random

def get_computer_pick(options):
    """Returns a random pick from the options list"""
    return random.choice(options)

def determine_winner(user_input, computer_pick):
    """Returns True if user wins, False otherwise"""
    winning_combos = {
        "rock": "scissors",
        "paper": "rock",
        "scissors": "paper"
    }
    return winning_combos.get(user_input) == computer_pick

def game_loop():
    options = ["rock", "paper", "scissors"]
    user_wins = 0
    computer_wins = 0

    while True:
        user_input = input("Type Rock/Paper/Scissors or Q to quit: ").lower()
        if user_input == "q":
            break

        if user_input not in options:
            print("Invalid input. Please try again.")
            continue

        computer_pick = get_computer_pick(options)
        print("Computer picked " + computer_pick + ".")

        if determine_winner(user_input, computer_pick):
            print("You won!")
            user_wins += 1
        else:
            print("You lost!")
            computer_wins += 1

    print("You won " + str(user_wins) + " times.")
    print("The computer won " + str(computer_wins) + " times.")
    print("Goodbye!")

if __name__ == "__main__":
    game_loop()
