# ai-memory-game-js
Memory Matching Cards Game, Version: 2.0

Simple artificial intelligence memory game where a user competes against 
an intelligent agent to find pairs of images. The agent and the user don't
have any information about the cards when the game begins. As they begin flipping
the cards, the agent starts storing the information of cards. 
(image + position -> card).

Choices that the AI takes:
 1) If the agent has information of where a pair is located, it automatically
    flips a pair by getting that information from automatic selection 
    function.
 2) If it doesn't have information about where a pair is located, it selects
    its first card randomly, then checks if it has information of where its
    pair is located. If it has that information, it will flip its pair as
    its second card, otherwise it will randomly flip its second card.
 3) If it doesn't have any information of any card, it selects its first
    and second card randomly (If it randomly selects a pair it's 
    coincidence, not a decision by memory).

 Rule A: Every time a card is flipped either by the user or the agent, the
         card information is stored so that the agent has its information
         for future flips.

Rule B: Agent always flips a card that has not been flipped before to not
         limit itself to acquire new information.
         It will only flip cards that have been flipped before if all the
         cards have been flipped already, which from that point on, the
         agent has all the information of where all the cards are located.

Scoring: The winner is the one who collects more pairs. There are no tides,
          because the number of pairs (cards/2) is an odd number.

Players: User and AI

Instructions:
 Each player selects two cards per turn to find a pair. If a pair is found,
 the player can flip again until a pair is not found. If a pair is not found,
 the other player has its turn to flip. User chooses who flips first before
 the game begins.
 
Code efficiency
 Negative aspects: (Besides the uncaught aspects)
 flippedPositions[] and flippedImages[] store information of cards that have
 been flipped. When pairs are found, they don't get removed from these
 arrays, they get pushed to removedPositions[] and removedImages[] so that
 the AI knows that they are "removed" from the game and are not available to
 flip anymore.
 
 So, if a card is flipped multiple times, it also gets stored multiple times
 and this makes the array to contain duplicates. This is not a big storage 
 consumption problem as the majority of duplicates will be because of the 
 user, and at least one duplicate per card because of the AI. 
 This is not fixed because this can be needed if statistics is added to the
 program about how many times the user flipped the same card, wasting its 
 turn to acquire new information, which is something that the AI doesn't do
 according to Rule B.
