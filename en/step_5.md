````markdown
## Tagging and being caught

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
    if <touching [Opponent v]?> then
        broadcast [tag opponent v]
    end
end
````

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

--- task ---

**Test your code.** Click the green flag, and make sure the opponent tagging is working, the score changes and the clone disappears when touched.

--- /task ---

### Being tagged

The rules of Kabaddi say that the player must tag opponents, but not get caught themselves. In this game, if more than one opponent is touching the player, they get caught. We need to make a way of telling if more than one opponent is touching the player.

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
set [touching v] to (0)
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
    if <(touching) > (1)> then
        broadcast [tag player v]
        set [touching v] to (0)
        wait (1) seconds
    end
end
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

--- task ---

**Test your code.** Click the green flag, and make sure the lives counter is working, and the player resets when you get tagged by more than one opponent.

--- /task ---

In the next step, make the player 'say kabaddi' using a key press!

--- save ---

