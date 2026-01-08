## Make the kabaddi timer

In kabaddi, the player has to keep repeating the word 'kabaddi' to show that they are not taking another breath. To simulate that, the player will need to press the space bar at least every second, or they will lose a life. 

--- task ---

Create a new `variable`{:class='block3variables'} called `kabaddi`. You will use this as a timer to make sure the player presses the 'kabaddi' button (the space bar) regularly, just like having to repeat "Kabaddi!" while you play.

--- /task ---

--- task ---

Add this code to the **Player** sprite, to simulate saying "Kabaddi!" by pressing <kbd>Space<kbd>:

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
    if <touching (Opponent v)?> then
        broadcast [tag opponent v]
    end
+    if <key (space v) pressed?> then
        set [kabaddi v] to (1)
    end
end
```

--- /task ---

--- task ---

On the **Stage**, add a new `broadcast`{:class='block3events'} with the message `kabbadi` to your 'start' script, so that the kabaddi timer (which you will set up next) starts running when the game starts:

![The Stage with a vertical green line across the centre.](images/stage.png)

```blocks3
when green flag clicked
set [lives v] to (5)
set [opponent tagged v] to (0)
set [touching v] to (0)
broadcast (start v)
+broadcast (kabaddi v)
forever
    if <(opponent tagged) = (7)> then
        broadcast (win v)
        wait (3) seconds
    end
    if <(lives) = (0)> then
        broadcast (lose v)
        wait (3) seconds
    end
    if <(touching) > (1)> then
        broadcast (tag player v)
        set [touching v] to (0)
        wait (1) seconds
    end
end
```

--- /task ---

--- task ---

Add this new code to the **Stage**, to make a one-second timer that keeps track of the player 'saying kabaddi':

![The Stage with a vertical green line across the centre.](images/stage.png)

```blocks3
when I receive (kabaddi v)
set [kabaddi v] to (1)
repeat until <(kabaddi) < (0)>
    wait (0.1) seconds
    change [kabaddi v] by (-0.1)
end
broadcast (tag player v)
broadcast (kabaddi v)
```

Players must press the space bar regularly (at least every second) to reset their timer, or they will be 'tagged' and lose a life. The timer will then start again when the `broadcast`{:class='block3events'} is sent.

--- /task ---

--- task ---

**Test your code.** Click on the green flag and make sure that the kabaddi timer works and that it resets when you press the space bar.

--- /task ---

```
```
