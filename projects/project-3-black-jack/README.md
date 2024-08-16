# Project: Blackjack

## Problem

Write a program that simulates a simplified version of the card game Blackjack. The game should have the following features:

- The game is played between a player and a dealer.
- The player starts with a balance of $100.
- The player can place bets in increments of $10 up to the total balance.
- The player and the dealer are each dealt two cards from a standard deck of 52 cards.
- The player's cards are dealt face up, while the dealer's cards are dealt with one card face up and one card face down.
- The value of cards 2 through 10 is their face value, the value of face cards (J, Q, K) is 10, and the value of an Ace is 11. The value of an Ace is reduced to 1 if the total card value exceeds 21.
- The player can choose to "hit" (draw a card) or "stand" (keep the current hand).
- The dealer cannot choose to hit or stand.
- The player wins the round if their total card value is closer to 21 than the dealer's total card value.
- The player wins the round if their total card value is exactly 21 (Blackjack) regardless of the dealer's total card value.
- The player loses the round if their total card value exceeds 21.
- The player ties with the dealer if both have the same total card value.
- The player wins their bet amount if they win the round and loses their bet amount if they lose the round.
- The player's balance is updated based on the outcome of the round.
- The game continues until the player chooses to quit or runs out of money.

### Example Output

```
Welcome to Blackjack!

Balance: $100

Place your bet (min: $10, max: $100): 50

Player's Hand: 10 ♠, 5 ♥
Dealer's Hand: 8 ♦, ?

Do you want to hit or stand? (h/s): h

Player's Hand: 10 ♠, 5 ♥, 7 ♣

Player's total: 22
Player busts! Dealer wins.

Balance: $50

Do you want to play again? (y/n): y

Balance: $50

Place your bet (min: $10, max: $50): 30

Player's Hand: 9 ♠, K ♥
Dealer's Hand: 3 ♦, ?

Do you want to hit or stand? (h/s): s

Player stands.

Player's total: 19
Dealer's total: 10

Player wins!

Balance: $80

Do you want to play again? (y/n): n

Goodbye!
```

### Answer

```python
import random

def create_deck():
    suits = ['♠', '♡', '♢', '♣']
    ranks = ['2', '3', '4', '5', '6', '7', '8', '9', '10', 'J', 'Q', 'K', 'A']
    deck = [{'rank': rank, 'suit': suit} for suit in suits for rank in ranks]
    random.shuffle(deck)
    return deck

def get_card_value(card):
    if card['rank'] in ['J', 'Q', 'K']:
        return 10
    elif card['rank'] == 'A':
        return 11
    else:
        return int(card['rank'])

def get_hand_value(hand):
    value = sum(get_card_value(card) for card in hand)
    num_aces = sum(1 for card in hand if card['rank'] == 'A')
    while value > 21 and num_aces:
        value -= 10
        num_aces -= 1
    return value

def display_hand(hand):
    return ', '.join(f"{card['rank']} {card['suit']}" for card in hand)

def play_blackjack():
    balance = 100
    print("\nWelcome to Blackjack!\n")
    while True:
        print(f"Balance: ${balance}\n")
        bet = int(input("Place your bet (min: $10, max: $100): "))
        while bet < 10 or bet > balance:
            bet = int(input("Invalid bet amount. Place your bet (min: $10, max: $100): "))
        deck = create_deck()
        player_hand = [deck.pop(), deck.pop()]
        dealer_hand = [deck.pop(), deck.pop()]
        print(f"\nPlayer's Hand: {display_hand(player_hand)}")
        print(f"Dealer's Hand: {dealer_hand[0]['rank']} {dealer_hand[0]['suit']}, ?\n")
        player_total = get_hand_value(player_hand)
        dealer_total = get_hand_value(dealer_hand)
        if player_total == 21:
            print("Player has Blackjack! Player wins.\n")
            balance += bet
        else:
            while player_total < 21:
                action = input("Do you want to hit or stand? (h/s): ")
                if action == 'h':
                    player_hand.append(deck.pop())
                    print(f"\nPlayer's Hand: {display_hand(player_hand)}")
                    player_total = get_hand_value(player_hand)
                    print(f"Player's total: {player_total}\n")
                    if player_total == 21:
                        print("Player has Blackjack! Player wins.\n")
                        balance += bet
                        break
                    elif player_total > 21:
                        print("Player busts! Dealer wins.\n")
                        balance -= bet
                        break
                else:
                    print("\nPlayer stands.\n")
                    print(f"Player's total: {player_total}\n")
                    break
            if player_total > dealer_total:
                print("Player wins!\n")
                balance += bet
            elif player_total == dealer_total:
                print("It's a tie!\n")
            else:
                print("Dealer wins.\n")
                balance -= bet
        print(f"Balance: ${balance}\n")
        play_again = input("Do you want to play again? (y/n): ")
        if play_again.lower() != 'y':
            print("\nGoodbye!")
            break

play_blackjack()
```
