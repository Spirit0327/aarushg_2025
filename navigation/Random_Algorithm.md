---
layout: page
title: Simulation & Random Algorithms HW Aarush Gowda Code Snippets
description: Homework submission for Simulation & Random Algorithms using Python.
permalink: /algorithm/
---

# Simulation & Random Algorithms Homework Submission


## Introduction

This notebook demonstrates several key concepts in simulation and random algorithms. In this submission, I have implemented the following:

- **Popcorn Hack #1:** A basic dice roll simulation using Python's `random` module.
- **Popcorn Hack #2:** A biased color generator that returns colors with specified probabilities.
- **Homework Hack #1:** A coin flip win simulation where two players flip coins until one reaches 3 heads—implemented in a sequential manner so that the first player to reach 3 heads wins.

All of these implementations showcase the use of randomness to simulate real-world processes and create unpredictability in games or simulations.

---

## Popcorn Hack #1: Dice Roll Simulation

This function simulates a 6-sided dice roll by randomly selecting an integer between 1 and 6.

```python
import random

def roll_dice():
    """
    Simulates a 6-sided dice roll.
    Returns a random integer between 1 and 6.
    """
    return random.randint(1, 6)

# Example usage:
print("Dice roll:", roll_dice())
```
```python
import random

def biased_color():
    """
    Generates a biased random color.
    - Red appears 50% of the time.
    - Blue appears 30% of the time.
    - Green, Yellow, and Purple share the remaining 20%.
    Returns a color as a string.
    """
    colors = ["Red", "Blue", "Green", "Yellow", "Purple"]
    # Define weights corresponding to each color:
    # Red: 0.50, Blue: 0.30, others: 0.0667 each (approx.)
    weights = [0.5, 0.3, 0.0667, 0.0667, 0.0667]
    return random.choices(colors, weights=weights, k=1)[0]

# Print 10 biased random colors
for _ in range(10):
    print("Biased color:", biased_color())
```

### Popcorn Hack #2: Biased Color Generator
```python
import random

def coin_flip_simulation():
    """
    Simulates a game where two players flip a coin.
    The first player to reach 3 heads wins.
    Each round, Player 1 flips first; if they reach 3 heads, they win immediately.
    Otherwise, Player 2 flips. The game reports the winner and the number of rounds taken.
    """
    player1_heads = 0
    player2_heads = 0
    rounds = 0
    
    while player1_heads < 3 and player2_heads < 3:
        rounds += 1
        print(f"Round {rounds}:")
        
        # Player 1 flips
        flip1 = random.choice(["heads", "tails"])
        print(f"  Player 1 flip: {flip1}")
        if flip1 == "heads":
            player1_heads += 1
            if player1_heads == 3:
                print(f"Player 1 wins! Reached 3 heads in {rounds} rounds.")
                return
        # Player 2 flips
        flip2 = random.choice(["heads", "tails"])
        print(f"  Player 2 flip: {flip2}")
        if flip2 == "heads":
            player2_heads += 1
            if player2_heads == 3:
                print(f"Player 2 wins! Reached 3 heads in {rounds} rounds.")
                return
        
        print(f"  Scores -> Player 1: {player1_heads}, Player 2: {player2_heads}\n")

# Run the coin flip simulation
coin_flip_simulation()
```
### Homework Hack #1: Coin Flip Win Simulation:
```python
import random

def coin_flip_simulation():
    """
    Simulates a game where two players flip a coin.
    The first player to reach 3 heads wins.
    Each round, Player 1 flips first; if they reach 3 heads, they win immediately.
    Otherwise, Player 2 flips. The game reports the winner and the number of rounds taken.
    """
    player1_heads = 0
    player2_heads = 0
    rounds = 0
    
    while player1_heads < 3 and player2_heads < 3:
        rounds += 1
        print(f"Round {rounds}:")
        
        # Player 1 flips
        flip1 = random.choice(["heads", "tails"])
        print(f"  Player 1 flip: {flip1}")
        if flip1 == "heads":
            player1_heads += 1
            if player1_heads == 3:
                print(f"Player 1 wins! Reached 3 heads in {rounds} rounds.")
                return
        # Player 2 flips
        flip2 = random.choice(["heads", "tails"])
        print(f"  Player 2 flip: {flip2}")
        if flip2 == "heads":
            player2_heads += 1
            if player2_heads == 3:
                print(f"Player 2 wins! Reached 3 heads in {rounds} rounds.")
                return
        
        print(f"  Scores -> Player 1: {player1_heads}, Player 2: {player2_heads}\n")

# Run the coin flip simulation
coin_flip_simulation()
```


