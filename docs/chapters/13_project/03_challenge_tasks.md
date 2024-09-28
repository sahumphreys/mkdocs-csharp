---
title: Challenge task -  Resume a game
---

# {{ title }}

1. Develop the part of the program that saves the progress of the game externally. Progress should be saved __after each turn__. If the player closes the game window (stops the execution) then all progress should be saved.

    !!! note
        Saving the state of the game at the end of each turn is straightforward (```SaveGame()``` method that saves the data for both the player and the computer to a file, simplest is a text file depending on your implementation) but do we need to consider it the game stops when the player is only part-way through entering a co-ordinate?  Easiest here to make an assumption that turn is lost ...

2. Develop the part of the program in such a way that when "resume a game" is selected, the player is presented with their progress from their previous game. The game should continue from this point.  

    !!! note
        We can make no assumptions about whose turn is next when the game resumes (though depending on your implementation the computer will go straight after the human player and it'll be quick, returning control back to the human player).  Do we need a variable holding e.g. ```currentPlayer```?
