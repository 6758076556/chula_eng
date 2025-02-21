# chula_eng
Demo repository for EngiLogic

import tkinter as tk
import random

# A sample dictionary mapping Thai consonants to their names.
flashcards = {
    'ก': 'gor kai',
    'ข': 'khor khai',
    'ค': 'khor khon',
    'ฆ': 'khor ra-khang',
    'ง': 'ngor ngu',
    # Add more consonants as needed
}

class FlashcardGame:
    def __init__(self, master):
        self.master = master
        master.title("Thai Consonant Flashcard Game")

        # Create a canvas to display the flashcard text.
        self.canvas = tk.Canvas(master, width=400, height=300)
        self.canvas.pack()

        # Create buttons for flipping the card and moving to the next card.
        self.flip_button = tk.Button(master, text="Flip", command=self.flip_card)
        self.flip_button.pack(side=tk.LEFT, padx=10, pady=10)

        self.next_button = tk.Button(master, text="Next", command=self.next_card)
        self.next_button.pack(side=tk.RIGHT, padx=10, pady=10)

        self.current_card = None
        self.is_flipped = False

        self.next_card()  # Start with a flashcard

    def next_card(self):
        # Choose a random flashcard (a tuple of (consonant, name)).
        self.current_card = random.choice(list(flashcards.items()))
        self.is_flipped = False
        self.show_front()

    def show_front(self):
        # Clear the canvas and show the Thai consonant.
        self.canvas.delete("all")
        self.canvas.create_text(200, 150, text=self.current_card[0],
                                font=("Helvetica", 72))

    def flip_card(self):
        if not self.is_flipped:
            # Clear the canvas and show the name of the consonant.
            self.canvas.delete("all")
            self.canvas.create_text(200, 150, text=self.current_card[1],
                                font=("Helvetica", 36))
            self.is_flipped = True

if __name__ == "__main__":
    root = tk.Tk()
    game = FlashcardGame(root)
    root.mainloop()
