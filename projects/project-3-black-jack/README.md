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
