## Stage Setup

Set up the game by drawing the green line and making all the variables you will need.

--- task ---

Paint the “green line”. This sets a safe zone for the player.

![](images/backdrop_menu_paint.png)

In the **Backdrops** editor, draw a vertical green line at x = –100. It should be 20 pixels thick.

![](images/backdrop_editor.png)

--- /task ---

--- task ---

Create five variables: `lives`{:class='block3variables'} , `opponent tagged`{:class='block3variables'}, `player tagged`{:class='block3variables'}, `touching`{:class='block3variables'}, and `kabaddi`{:class='block3variables'}. 

![](images/variables.png)

These variables will control game state, collisions, and scoring.

--- /task ---

--- task ---

Write the game “Start” script:

![](images/stage.png)

```blocks3
when green flag clicked
set [lives v] to (5)
set [opponent tagged v] to (0)
set [player tagged v] to (0)
set [touching v] to (0)
broadcast [start v]
broadcast [kabaddi v]
```

This prepares the game state and triggers the start and countdown broadcasts. 

FIrst, it gives the player 5 lives and resets all the variables to 0. Then, it sends two broadcasts out - one which starts all the other sprites, and one which will eventually start a timer to make sure the player is 'saying kabaddi' while playing.

--- /task ---

In the next step, make the controls for your player!

--- save ---