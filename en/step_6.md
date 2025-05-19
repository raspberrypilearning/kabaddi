## Make the Kabaddi timer

In the rules of Kabaddi, the player has to keep repeating the word 'Kabaddi' over and over to show they aren't taking another breath. We're going to simulate that by needing the player to press space every second, or lose a life. 

--- task ---

Create a new `variable`{:class='block3variables'} called `kabaddi`. We will use this as a timer to make sure the player presses the 'kabaddi' button (space bar) every so often, just like having to say 'Kabaddi!' while you play.

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
    end
end
```

--- /task ---

--- task ---

On the **Stage**, add this `broadcast`{:class='block3events'} to your start script, to make sure our Kabaddi timer starts counting when the game starts:

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

Players must press space regularly (every second) to reset their timer, or they'll get 'tagged' and lose a life. The timer then starts itself again with the `broadcast`{:class='block3events'}.

--- /task ---

--- task ---

**Test your code.** Click the green flag, and make sure the Kabaddi timer is working, and resets when you press the space bar.

--- /task ---

```
```
