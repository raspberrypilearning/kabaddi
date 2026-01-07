## Tagging and being caught

Make the tagging and scoring work.

### Tagging opponents

--- task ---

Create a new `broadcast`{:class='block3events'} with the message `tag opponent`. This will be used to keep track of how many opponents the player tags.

--- /task ---

--- task ---

Add this code to the **Player** sprite, so that it identifies when the player tags an opponent:

![The Player sprite.](images/avery.png)

```blocks3
when I receive [start v]
set size to (25)%
go to x:(-160) y:(0)
wait (1) seconds
repeat until <(lives) = (0)>
    if <key (up arrow v) pressed?> then 
        change y by (10)
    end
    if <key (down arrow v) pressed?> then 
        change y by (-10)
    end
    if <key (right arrow v) pressed?> then 
        change x by (10)
    end
    if <key (left arrow v) pressed?> then 
        change x by (-10)
    end
+    if <touching (Opponent v)?> then
        broadcast (tag opponent v)
+    end
end
```

--- /task ---

--- task ---

On the **Opponent** sprite, add this new code to remove opponents who are tagged:

![The Opponent sprite.](images/opponent.png)

```blocks3
when I receive (tag opponent v)
if <touching (Player v)> then
    delete this clone
end
```

--- /task ---

--- task ---

The Stage will handle the scoring in the game. Add these blocks to the **Stage**:

![The Stage with a vertical green line across the centre.](images/stage.png)

```blocks3
when I receive (tag opponent v)
change [opponent tagged v] by (1)
```

--- /task ---

--- task ---

**Test your code.** Click on the green flag and make sure the opponent tagging works: the score should change and each clone should disappear when touched by the player.

--- /task ---

### Being caught

In kabaddi, the player must tag opponents, but not get caught themselves. In this game, if more than one opponent is touching the player, the player has been caught. You need to make a way to identify if more than one opponent is touching the player.

--- task ---

On the **Stage**, make a new `variable`{:class='block3variables'} called `touching`.

--- /task ---

--- task ---

Add this code to the **Opponent** sprite, so that the game checks if more than one opponent is touching the player:

![The Opponent sprite.](images/opponent.png)

```blocks3
when I start as a clone
repeat until <(lives) = (0)>
    if <touching (Player v)?> then
        change [touching v] by (1)
        wait until <not <touching (Player v)?>>
        change [touching v] by (-1)
    end
end
```

--- /task ---

--- task ---

Create a new `broadcast`{:class='block3events'} with the message `tag player`.

--- /task ---

--- task ---

Add this code to the 'start' script on the **Stage**, to make sure that the `touching`{:class='block3variables'} variable is set to `0` when the game starts, and that the game identifies when more than one opponent is touching the player (`touching`{:class='block3variables'} `>`{:class='block3operators'} `1`).

![The Stage with a vertical green line across the centre.](images/stage.png)

```blocks3
when green flag clicked
set [lives v] to (5)
set [opponent tagged v] to (0)
+set [touching v] to (0)
broadcast (start v)
forever
    if <(opponent tagged) = (7)> then
        broadcast (win v)
        wait (3) seconds
    end
    if <(lives) = (0)> then
        broadcast (lose v)
        wait (3) seconds
    end
+    if <(touching) > (1)> then
        broadcast (tag player v)
        set [touching v] to (0)
        wait (1) seconds
+    end
end
```

--- /task ---

If more than one opponent touches the player, the player has been 'tagged' and needs to lose a life and go back across the green line.

--- task ---

Add this code to the **Player** sprite, so that the player moves back to the starting position and loses a life if they are tagged:

![The Player sprite.](images/avery.png)

```blocks3
when I receive (tag player v)
go to x:(-160) y:(0)
change [lives v] by (-1)
```

--- /task ---

--- task ---

**Test your code.** Click on the green flag and make sure that the lives counter works and the player moves back across the green line when they are caught by more than one opponent.

--- /task ---

In the next step, you will make the player 'say kabaddi' using a key press.

--- save ---

