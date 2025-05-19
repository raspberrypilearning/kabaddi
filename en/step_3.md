## Player Setup and Controls

Add the player sprite and make it move around.

--- task ---

Import the player sprite from the sprite menu. Choose anything you like — in this example we will use the `Avery walking` sprite:

![](images/sprite-choose.png)
![](images/avery.png)

Rename this sprite `player`.

![](images/rename-player.png)

--- /task ---

--- task ---

Stage the “start” handler for the player:

![](images/avery.png)

```blocks3
when I receive [start v]
set size to (25)%
go to x:(-160) y:(0)
wait (1) seconds
```

This ensures the player begins in the correct position and scale.

--- /task ---

--- task ---

Add arrow-key movement:

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
end
```

This allows the player to move around the stage using the keyboard.

--- /task ---

--- task ---

Add the code now that will stop the game if the player wins or loses:

![](images/avery.png)

```blocks3
when I receive [lose v]
say [TRY AGAIN!] for (2) seconds
stop [all v]

when I receive [win v]
say [YOU WIN!] for (2) seconds
stop [all v]
```

--- /task ---

--- task ---

**Test your code.** Click the green flag and make sure you can control the player sprite.

--- /task ---

In the next step, make opponents who will chase the player!

--- save ---