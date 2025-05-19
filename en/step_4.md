## Add Opponents

Make opponents appear and chase the player.

--- task ---

Import an opponent sprite. In this example, we use the `Character 1` sprite:

![](images/sprite-choose.png)  

![](images/opponent.png)

Rename this sprite to `opponent`.

![](images/rename-opponent.png)

--- /task ---

--- task ---

Add a setup script for the opponent:

![](images/opponent.png)

```blocks3
when I receive [start v]
set size to (25)%
set rotation style [left-right v]
hide
repeat (7)
    create clone of [myself v]
end
````

This prepares the base sprite to clone without showing it.

--- /task ---

--- task ---

Give each clone a random look and location:

![](images/opponent.png)

```blocks3
when I start as a clone
switch costume to (pick random (1) to (13))
go to x:(pick random (-100) to (240)) y:(pick random (-180) to (180))
show
repeat until <(lives) = (0)>
    point towards [Player v]
    turn right (pick random (-70) to (70)) degrees
    move (2) steps
    if on edge, bounce
end
delete this clone
```

Each clone will chase the player.

--- /task ---

In the next step, have the opponents catch the player, and the player tag the opponents!

--- save ---
