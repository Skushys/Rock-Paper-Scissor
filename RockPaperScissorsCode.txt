import tkinter as tk
import random

# Game logic function
def play(user_choice):
    computer_options = ["Rock", "Paper", "Scissors"]
    computer_choice = random.choice(computer_options)

    result_text = f"You chose: {user_choice}\nComputer chose: {computer_choice}\n"

    if user_choice == computer_choice:
        result_text += "It's a tie!"
    elif (user_choice == "Rock" and computer_choice == "Scissors") or \
         (user_choice == "Paper" and computer_choice == "Rock") or \
         (user_choice == "Scissors" and computer_choice == "Paper"):
        result_text += "You win!"
    else:
        result_text += "Computer wins!"

    result_label.config(text=result_text)

# Create GUI window
root = tk.Tk()
root.title("Rock, Paper, Scissors")

# Instructions label
instructions = tk.Label(root, text="Choose your move:")
instructions.pack()

# Buttons for user choices
choices = ["Rock", "Paper", "Scissors"]
for choice in choices:
    tk.Button(root, text=choice, width=15, command=lambda c=choice: play(c)).pack(pady=5)

# Result label
result_label = tk.Label(root, text="", font=("Arial", 12), pady=10)
result_label.pack()

# Start GUI
root.mainloop()