## Set up the player and controls

Add a player sprite and make it move around.

--- task ---

Delete the **Sprite1** sprite — click on the **Delete** icon on the thumbnail:

![The Scratch cat sprite thumbnail with the name Sprite1, with a 'Delete' icon.](images/scratch-thumbnail.png)

--- /task ---

--- task ---

Use the **Choose a Sprite** menu to add a **player** sprite. Choose anything you like — in this example, we will use the **Avery Walking** sprite:

![The 'Choose a Sprite' icon highlighted.](images/sprite-choose.png)

Rename the sprite `Player`.

![The sprite name set to 'Player' in the Sprite pane.](images/rename-player.png)

![The Avery Walking sprite is now named Player.](images/avery.png)

--- /task ---

--- task ---

Create the 'start' script for the player:

![The Player sprite.](images/avery.png)

```blocks3
when I receive [start v]
set size to (25)%
go to x:(-160) y:(0)
wait (1) seconds
```

This makes sure that the player begins in the correct position and scale.

--- /task ---

--- task ---

Add arrow key movement:

![The Player sprite.](images/avery.png)

```blocks3
when I receive [start v]
set size to (25)%
go to x:(-160) y:(0)
wait (1) seconds
+repeat until <(lives) = (0)>
    if <key (up arrow v) pressed?> then // allows player to move up
        change y by (10)
    end
    if <key (down arrow v) pressed?> then // allows player to move down
        change y by (-10)
    end
    if <key (right arrow v) pressed?> then // allows player to move right
        change x by (10)
    end
    if <key (left arrow v) pressed?> then // allows player to move left
        change x by (-10)
    end
+end
```



--- /task ---

--- task ---

Add code to stop the game if the player wins or loses:

![The Player sprite.](images/avery.png)

```blocks3
when I receive (lose v)
say [TRY AGAIN!] for (2) seconds
stop [all v]

when I receive (win v)
say [YOU WIN!] for (2) seconds
stop [all v]
```

--- /task ---

--- task ---

**Test your code.** Click on the green flag and make sure you can control the **Player** sprite.

--- /task ---

In the next step, you will make opponents who will chase the player!

--- save ---