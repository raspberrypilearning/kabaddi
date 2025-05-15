## Game Interactions

Make the tagging and scoring work, and add the Kabaddi timer.

--- task ---

Add this code to the **Player** sprite, so it registers if the player tags an opponent:

![](images/avery.png)

```blocks3
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
+    if <touching [Opponent v]?> then
        broadcast [tag opponent v]
+    end
end
```

--- /task ---

The rules of Kabaddi says that the player must tag opponents, but not get caught themselves. In this game; if more than one opponent is touching the player, they get caught.

--- task ---

Add this code to the **Opponent** sprite, so the game is checking if more than one opponent is touching the player:

![](images/opponent.png)

```blocks3
when I start as a clone
repeat until <(lives) = (0)>
    if <touching [Player v]?> then
        change [touching v] by (1)
        wait until <not <touching [Player v]?>>
        change [touching v] by (-1)
    end
end
```

--- /task ---

If more than one opponent touches the player, they need to lose a life and go back across the line. 

--- task ---

Add that code to the **Player** now:

![](images/avery.png)

```blocks3
when I receive [tag player v]
go to x:(-160) y:(0)
change [lives v] by (-1)
```

--- /task ---

--- task ---

The Stage handles the scoring in our game. Add these blocks to the **Stage**:

![](images/stage.png)

```blocks3
when I receive [tag opponent v]
change [opponent tagged v] by (1)

when I receive [tag player v]
change [player tagged v] by (1)

```

--- /task ---

### Kabaddi timer and reset

In the rules of Kabaddi, the player has to keep repeating the word 'Kabaddi' over and over to show they aren't taking another breath. We're going to simulate that by needing the player to press space every second, or lose a life. 

--- task ---

Add this code to the player, to simulate saying 'kabaddi' by pressing `space`:

![](images/avery.png)

```blocks3
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
    if <touching [Opponent v]?> then
        broadcast [tag opponent v]
    end
+    if <key [space v] pressed?> then
        set [kabaddi v] to (1)
+    end
end
```
--- /task ---

--- task ---

Add this code to the **Stage**, to make a one-second timer that keeps track of the player 'saying kabaddi':

![](images/stage.png)

```blocks3
when I receive [kabaddi v]
set [kabaddi v] to (1)
repeat until <(kabaddi) < (0)>
    wait (0.1) seconds
    change [kabaddi v] by (-0.1)
end
broadcast [tag player v]
broadcast [kabaddi v]
```

Players must press space regularly to reset their timer, or they'll lose a life.

--- /task ---

--- save ---