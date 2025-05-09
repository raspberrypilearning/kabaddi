## Stage Setup
Set up the game by drawing the green line, making the needed variables, and writing the starting code.

--- task ---

Paint the “green line”

In the Backdrops editor, draw a vertical green line at x = –100.  
This sets a visual reference for safe/unsafe zones.

--- /task ---

--- task ---

Test the green line

Switch to that backdrop and verify the line is exactly where you expect.

--- /task ---

--- task ---

Create all Stage variables

Create five variables: `lives`, `opponent tagged`, `player tagged`, `touching`, and `kabaddi`.  

These variables will control game state, collisions, and scoring.

--- /task ---

--- task ---

Write the game “Start” script

```scratchblocks
when green flag clicked
set [lives v] to (5)
set [opponent tagged v] to (0)
set [player tagged v] to (0)
set [touching v] to (0)
broadcast [start v]
broadcast [kabaddi v]
forever
    // win / lose / simultaneous-touch logic here…
end
```

This prepares the game state and triggers the start and countdown.

--- /task ---

--- task ---

Test initialisation and broadcast logic

Click green-flag, then pause to confirm all values and broadcasts are correct.

--- /task ---

--- save ---
