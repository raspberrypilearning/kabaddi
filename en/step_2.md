## Stage Setup
Set up the game by drawing the green line, making the needed variables, and writing the starting code.

--- task ---

Paint the “green line”.

In the Backdrops editor, draw a vertical green line at x = –100.  It should be 20 pixels thick.

![](images/backdrop_menu_paint.png)


This sets a safe zone for the player.

![](images/backdrop_editor.png)

--- /task ---

--- task ---

Create five variables: `lives`, `opponent tagged`, `player tagged`, `touching`, and `kabaddi`. 

![](images/variables.png)

These variables will control game state, collisions, and scoring.

--- /task ---

--- task ---

Write the game “Start” script:

![](images/stage.png)

```scratchblocks
when green flag clicked
set [lives v] to (5)
set [opponent tagged v] to (0)
set [player tagged v] to (0)
set [touching v] to (0)
broadcast [start v]
broadcast [kabaddi v]
```

This prepares the game state and triggers the start and countdown broadcasts.

--- /task ---

Next, create the game counters using the variables which will keep track of winning and losing, and whether more than one clone is touching the player sprite.

--- task ---
Add a forever block to the bottom of the 'Start' script:

![](images/stage.png)

```scratchblocks
when green flag clicked
set [lives v] to (5)
set [opponent tagged v] to (0)
set [player tagged v] to (0)
set [touching v] to (0)
broadcast [start v]
broadcast [kabaddi v]
+forever
end
```
--- /task ---

--- task ---

Create the 'win' counter inside the forever loop. If the player tags all 7 clones, they win:

![](images/stage.png)

```scratchblocks
forever
+    if <(opponent tagged) = (7)> then
+        broadcast [win v]
+        wait (3) seconds
    end
end
```

--- /task ---

--- task ---

Create the 'lose' counter inside the forever loop:

![](images/stage.png)

```scratchblocks
forever
    if <(opponent tagged) = (7)> then
        broadcast [win v]
        wait (3) seconds
    end
+     if <(lives) = (0)> then
+        broadcast [lose v]
+        wait (3) seconds
    end
end
```

--- /task ---

--- task ---

Add the 'touch' counter to the forever loop. This tracks how many clones are touching the player sprite. If more than one clone is touching it, the player is 'tagged':

![](images/stage.png)

```scratchblocks
forever
    if <(opponent tagged) = (7)> then
        broadcast [win v]
        wait (3) seconds
    end
     if <(lives) = (0)> then
        broadcast [lose v]
        wait (3) seconds
    end
+    if <(touching) > (1)> then
+        broadcast [tag player v]
+        set [touching v] to (0)
+        wait (1) seconds
    end
end
```

--- /task ---


--- task ---

Test your game

Click green-flag and check all values and broadcasts are correct.

--- /task ---

--- save ---
