## Player Mechanics

Create the player sprite, make it move with the keyboard, and add what happens if the player wins or loses.

--- task ---

Import the player sprite from the sprite menu. Choose anything you like — in this example we will use the `Avery walking` sprite:

![](images/sprite-choose.png)
![](images/avery.png)

--- /task ---

--- task ---

Rename this sprite `player`.

![](images/rename-player.png)

--- /task ---

--- task ---

Stage the “start” handler for the player:

![](images/avery.png)

```blocks3-high-contrast
when I receive [start v]
set size to (25)%
go to x:(-160) y:(0)
wait (1) seconds
```

This ensures the player begins in the correct position and scale.

--- /task ---

--- task ---

Test player position and size.

Click the green flag and ensure correct placement and scaling.

--- /task ---

--- task ---

Add arrow-key movement:

![](images/avery.png)

```blocks3-high-contrast
when I receive [start v]
set size to (25)%
go to x:(-160) y:(0)
wait (1) seconds
+repeat until <(lives) = (0)>
+    if <key [up arrow] pressed?> then
+        change y by (10)
+    end
+    if <key [down arrow] pressed?> then
+        change y by (-10)
+    end
+    if <key [right arrow] pressed?> then
+        change x by (10)
+    end
+    if <key [left arrow] pressed?> then
+        change x by (-10)
+    end
+end
```

This allows the player to move around the stage using the keyboard.

--- /task ---

--- task ---

Test player movement

Press arrow keys—verify movement is smooth and accurate.

--- /task ---

--- task ---

Add Kabaddi-timer reset:

![](images/avery.png)

```blocks3-high-contrast
when I receive [start v]
set size to (25)%
go to x:(-160) y:(0)
wait (1) seconds
repeat until <(lives) = (0)>
    if <key [up arrow] pressed?> then
        change y by (10)
    end
    if <key [down arrow] pressed?> then
        change y by (-10)
    end
    if <key [right arrow] pressed?> then
        change x by (10)
    end
    if <key [left arrow] pressed?> then
        change x by (-10)
    end
+    if <key [space v] pressed?> then
+       set [kabaddi v] to (1)
+    end
end
```

This resets the kabaddi countdown when the player 'calls out' by pressing the space bar.

--- /task ---

--- task ---

Test spacebar and kabaddi reset.

Press or hold space—check that `kabaddi` resets to 1.

--- /task ---

--- task ---

Add a `when I receive [tag player]` script to reset the player:

![](images/avery.png)

```blocks3-high-contrast
+when I receive [tag player v]
+go to x:(-160) y:(0)
+play sound [pop v]
```

This moves the player back to the start when they’re tagged.

--- /task ---

--- task ---

Add a `when I receive [win]` script:

![](images/avery.png)

```blocks3-high-contrast
+when I receive [win v]
+say [You win!] for (2) seconds
+stop [all v]
```

This shows a win message to the player and ends the game, if the win condition is met on the stage.

--- /task ---

--- task ---

Add a `when I receive [lose]` script:

![](images/avery.png)

```blocks3-high-contrast
+when I receive [lose v]
+say [You lose!] for (2) seconds
+stop [all v]
```

This shows a loss message to the player and ends the game.

--- /task ---

--- task ---

Test player tag and endgame handlers

Manually broadcast each message to verify the sprite resets, messages appear, and the game ends. You can 

--- /task ---

--- save ---