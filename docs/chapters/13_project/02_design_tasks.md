---
title: Design Tasks
---

# {{ title }}

Go and get that pen and paper!

What are your initial thoughts about the problem?  What data needs to be handled e.g. the playing grid(s), the coordinates for firing etc..?  How will that data be structured?  What algorithms do you expect will be required e.g. Fire(), DisplayGrid(), GetSquareToHit(), SaveGameState(), Quit() etc..

There will be two players, each player will have their own grids and methods to e.g. ```PlaceBoats()```, ```Fire()``` etc..  How might the ```Player``` be structured?

1. Create a flowchart of the game play. The first screen presented to the user should be the __main menu__ where the user can choose from one of the following options:

   - New Game
   - Resume Game
   - Read Instructions
   - Quit Game

2. Design the menu screen and implement it.  (Hints:  The user should always be taken back to the main menu following any of the options. Create method stubs for NewGame(), ResumeGame() etc and test your menu).

3. Develop the part of the program in such a way that when "New Game" is selected, the player is presented with a blank fleet grid. The program should:

    - Prompt the player to enter coordinates for each ship
    - Check if a ship has already been placed in the specified location
    - Display each ship on the fleet grid after each entry
    - Only allow the player to enter five ship locations

    !!! tip
        There is scope here for creating a data structure (```struct```) to hold the player information including their name, their playing grid etc..  Remember though, a ```struct``` is a value data type, if you pass it into a method and want it to get updated you MUST use the ```ref``` parameter to pass it in by reference and not by value.

    !!! tip
        The columns are labelled by letter, A-H; the rows numerically.  This could be entered separately (i.e. "Enter row >", "Enter column >") or as one string. If the latter (which is easier for the user?) the row will need to separated from the column (e.g. ```row = position[0];```).  But what about the column: a letter?  This needs to be converted into an integer representing the column number (A=0,B=1 etc..).  One approach, but not the only one, would be to create an array of the letters (```char[] colArray = { 'A', 'B', 'C', 'D', 'E', 'F', 'G', 'H' };```).  Then use the ```IndexOf()``` method to return the found position:
        ```cs
        char[] colArray = { 'A', 'B', 'C', 'D', 'E', 'F', 'G', 'H' };
        // ...
        int col = Array.IndexOf(colArray,position[1]);
        ```

    The rest of these requirements should be straightforward ... except ... validation of user input.  Did you think of this in your pen and paper planning? Not tricky but need to check they have entered a valid digit followed by a valid character.  One possibility would be use a __regular expression__.

4. Develop the part of the program that randomly selects five unique locations for the computer's fleet. These locations should not be revealed to the player. __NOTE__: The computer's fleet will not be displayed to the user at any point in the game. For testing purposes it will be necessary to display the locations but these should not appear in the finished game.

    !!! tip
        Displaying the grid is used frequently.  There are 2 types of grid and two players.  Generalise this into one method that takes as parameters (a) the grid belonging to a particular player; (b) the player; and, optionally, (c) a label for the grid (e.g. "FLEET GRID", "TARGET GRID")

    !!! tip
        Consider using __constants__ in your program.  This is useful for e.g. the number of rows and column, the "playing pieces" i.e. 'S' for a ship, 'H' for a hit etc..  These could be put into their own ```struct``` ... Then, should you wish to change the size of the grid, or the total number of ships to be placed, there is just one place to update rather than several.  Similarly, it may be appropriate to use an ```enum``` for the states of each square in the grid.

5. Develop the part of the program that displays a blank target tracker for the player.

    !!! note
        This should be trivial if you've followed the earlier tip about displaying a grid.

6. Develop the part of the program that allows the player to take their turn. The program should:

    - Prompt for the target coordinates. NOTE: The program should not allow the player to select the same coordinates twice.  
    - Check if the target is a hit or a miss
    - If the target is a hit then an H should be displayed on the target tracker
    - If the target is a miss then an M should be displayed on the target tracker

    !!! tip
        You've already asked the player for coordinates!  Remember, "Don't Repeat Yourself".  Looks like an opportunity for a method!  Here's a chance to learn something new:  __tuples__.  A tuple is a lightweight data structure used to group multiple data elements together:

        ```cs
            (int, double) tuple1 = (42, 2.57);
        ```

    We can write a method that returns a tuple e.g.

    ```cs
        static (int,int) GetPosition()
        {
            // body of method
            return (row, col);
        }
    ```

    This method can then be used whenever you ask the user for some coordinates. (Don't forget to validate the input too).

7. Develop the part of the program that allows the computer to take its turn. The program should:

    - Randomly generate target coordinates. NOTE: The program should not allow the computer to select the same location twice.
    - Display the coordinates to the player.
    - Check if the target is a hit or a miss.
    - If the target is a hit then an H should replace the S on the player's fleet grid.  
    - If the target is a miss then this should be recorded by the program. There is no need to display a miss on the player's fleet grid.

8. Develop the part of the program that continues to play the game until there is a winner. A game has been won when a player has sunk all of their opponent's battle boats. The winner of the game should be displayed to the player.
