import time


player_name = ""
inventory = []


def intro():
    global player_name
    print("Welcome to the Text-Based Adventure Game!")
    player_name = input("Enter your character's name: ")
    time.sleep(1)
    print(f"Hello, {player_name}! You find yourself in a mysterious forest.")
    time.sleep(1)
    print("Your goal is to find the lost treasure and make it out alive.")
    time.sleep(1)
    print("Let's begin...\n")
    start_journey()

def start_journey():
    print(f"You stand at a crossroads, {player_name}. You can go 'left' or 'right'.")
    choice = input("Which way do you choose? ").lower()
    if choice == "left":
        left_path()
    elif choice == "right":
        right_path()
    else:
        print("Invalid choice. Try again.")
        start_journey()

def left_path():
    print("You chose to go left and come across an old bridge.")
    time.sleep(1)
    print("You can 'cross the bridge' or 'explore the forest nearby'.")
    choice = input("What will you do? ").lower()
    if choice == "cross the bridge":
        print("You cross the bridge and continue your journey.")
        inventory.append("Golden Key")
        continue_journey()
    elif choice == "explore the forest nearby":
        print("You find a hidden chest and inside it, you discover a mysterious amulet.")
        inventory.append("Mysterious Amulet")
        continue_journey()
    else:
        print("Invalid choice. Try again.")
        left_path()

def right_path():
    print("You chose to go right and discover a dark cave entrance.")
    time.sleep(1)
    print("You can 'enter the cave' or 'bypass the cave and keep walking'.")
    choice = input("What will you do? ").lower()
    if choice == "enter the cave":
        print("You enter the dark cave, and it leads you to a chamber filled with jewels.")
        inventory.append("Jewels")
        continue_journey()
    elif choice == "bypass the cave and keep walking":
        print("You decide to bypass the cave and continue your journey.")
        continue_journey()
    else:
        print("Invalid choice. Try again.")
        right_path()

def continue_journey():
    print("You continue your journey and find an ancient door.")
    time.sleep(1)
    print("You notice that the door requires a key to unlock it.")
    time.sleep(1)
    print("You check your inventory and find the following items:")
    for item in inventory:
        print(f"- {item}")
    if "Golden Key" in inventory:
        print("You can 'use the Golden Key' to unlock the door.")
        choice = input("What will you do? ").lower()
        if choice == "use the golden key":
            open_door()
        else:
            print("Invalid choice. Try again.")
            continue_journey()
    else:
        print("You need a key to unlock the door. You must go back and find one.")
        left_path()

def open_door():
    print("You use the Golden Key to unlock the door, and it creaks open.")
    time.sleep(1)
    print("Inside, you find the lost treasure!")
    time.sleep(1)
    ending = input("Congratulations! You've found the treasure!\nThere are multiple endings in this game. Choose an ending (A, B, or C): ").lower()
    if ending == "a":
        print(f"Ending A: {player_name} escapes with the treasure and lives a wealthy life!")
    elif ending == "b":
        print(f"Ending B: {player_name} shares the treasure with the villagers and becomes a local hero.")
    elif ending == "c":
        print(f"Ending C: {player_name} decides to leave the treasure behind, valuing the adventure over riches.")
    else:
        print(f"Invalid choice. Choose an ending (A, B, or C).")
        open_door()


intro()
