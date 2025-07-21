## Add Opponents

Make opponents appear and chase the player.

--- task ---

Import an opponent sprite. In this example, we use the `Character 1` sprite:

![Sidebar menu with “Choose a Sprite” highlighted.](images/sprite-choose.png)  

![Sprite of a person in a wheelchair, labelled “opponent”](images/opponent.png)

Rename this sprite to `Opponent`.

![](images/rename-opponent.png)

--- /task ---

--- task ---

Add a setup script for the opponent:

![Sprite of a person in a wheelchair, labelled “opponent”](images/opponent.png)

```blocks3
when I receive [start v]
set size to (25)%
set rotation style [left-right v]
hide // This prepares the base sprite to clone without showing it.
repeat (7)
    create clone of [myself v]
end
````

--- /task ---

--- task ---

Give each clone a random look and location:

![Sprite of a person in a wheelchair, labelled “opponent”](images/opponent.png)

```blocks3
when I start as a clone
switch costume to (pick random (1) to (13))
go to x:(pick random (-100) to (240)) y:(pick random (-180) to (180))
show
repeat until <(lives) = (0)>
    point towards (Player v) // Each clone will chase the player.
    turn right (pick random (-70) to (70)) degrees
    move (2) steps
    if on edge, bounce
end
delete this clone
```

--- /task ---

--- task ---

**Test your code.** Click the Green flag and watch the opponents rush towards you!

--- /task ---

--- task ---

Now, add this new code **inside** your `repeat until (lives=0)` loop, so that if the opponents touch the green line, they are moved away:

```blocks3
when I start as a clone
switch costume to (pick random (1) to (13))
go to x:(pick random (-100) to (240)) y:(pick random (-180) to (180))
show
repeat until <(lives) = (0)>
    point towards (Player v) // Each clone will chase the player.
    turn right (pick random (-70) to (70)) degrees
    move (2) steps
    if on edge, bounce
    +	if <touching color ( #00ff00) > then
	change x by (100)
	change y by (pick random (-180) to (180)
    end
end
delete this clone
```

--- /task ---

--- task ---

**Test your code.** Click the Green flag and watch the opponents rush towards you, but bounce off the green line!

--- /task ---

In the next step, have the opponents catch the player, and the player tag the opponents!

--- save ---
