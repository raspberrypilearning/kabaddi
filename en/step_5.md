## Game Interactions

Make the tagging and scoring work, and add the Kabaddi timer.

### Tagging opponents

--- task ---

Create a new `broadcast`{:class='block3events'} which says `tag opponent`. This will be used to keep track of how many opponents you catch.

--- /task ---

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

--- task ---

On the **Opponent** sprite, add this new code to remove opponents who get tagged:

![](images/opponent.png)

```blocks3
when I receive [tag opponent v]
if <touching [player v]> then
delete this clone 
end
```

--- /task ---

--- task ---

The Stage handles the scoring in our game. Add these blocks to the **Stage**:

![](images/stage.png)

```blocks3
when I receive [tag opponent v]
change [opponent tagged v] by (1)

```

--- /task ---

### Being tagged

The rules of Kabaddi say that the player must tag opponents, but not get caught themselves. In this game; if more than one opponent is touching the player, they get caught. We need to make a way of telling of more than one opponent is touching the player.

--- task ---

On the **Stage**, make a new `variable`{:class='block3variables'} called `touching`.

--- /task ---

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

--- task ---

Create a new `broadcast`{:class='block3events'} called `tag player`.

--- /task ---

--- task ---

Add this code to the start script on the **Stage**, to make sure the variable is `0` when the game starts, and that if more than one opponent is touching the player (`touching > 1`) then they get 'tagged' and lose a life. 

![](images/stage.png)

```blocks3
when green flag clicked
set [lives v] to (5)
set [opponent tagged v] to (0)
+set [touching v] to (0)
broadcast [start v]
forever
if <(opponent tagged) = (7)> then
    broadcast [win v]
    wait (3) seconds
end
if <(lives) = (0)> then
    broadcast [lose v]
    wait (3) seconds
end
+if <(touching) > (1)> then
    broadcast [tag player v]
    set [touching v] to (0)
    wait (1) seconds
+end
```

--- /task ---

Now, if more than one opponent touches the player, they need to lose a life and go back across the line. 

--- task ---

Add this code to the **Player** now, so it can react properly if tagged:

![](images/avery.png)

```blocks3
when I receive [tag player v]
go to x:(-160) y:(0)
change [lives v] by (-1)
```

--- /task ---

### Kabaddi timer and reset

In the rules of Kabaddi, the player has to keep repeating the word 'Kabaddi' over and over to show they aren't taking another breath. We're going to simulate that by needing the player to press space every second, or lose a life. 

--- task ---

Create a new `variable` called `kabaddi`. We will use this as a timer to make sure the player presses the 'breathe' button every so often, just like having to say 'Kabaddi!' while you play.

--- /task ---

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

On the **Stage**, add this block to your start script to make sure out Kabaddi timer starts counting when the game starts:

```blocks3
when green flag clicked
set [lives v] to (5)
set [opponent tagged v] to (0)
set [touching v] to (0)
broadcast [start v]
+broadcast [kabaddi v]
forever
if <(opponent tagged) = (7)> then
    broadcast [win v]
    wait (3) seconds
end
if <(lives) = (0)> then
    broadcast [lose v]
    wait (3) seconds
end
end
```

--- /task ---

--- task ---

Add this new code to the **Stage**, to make a one-second timer that keeps track of the player 'saying kabaddi':

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

Players must press space regularly (every second) to reset their timer, or they'll get 'tagged' and lose a life.

--- /task ---

--- save ---