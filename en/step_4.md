## Add opponents

Make opponents appear and chase the player.

--- task ---

Add an **opponent** sprite. In this example, we will use the **Characters 1** sprite (with the costume **character1-e**):

![The 'Choose a Sprite' icon highlighted.](images/sprite-choose.png)  

Rename the sprite `Opponent`.

![The sprite name set to 'Opponent' in the Sprite pane.](images/rename-opponent.png)

![The Characters 1 sprite is now named Opponent.](images/opponent.png)

--- /task ---

--- task ---

Add a setup script for the **Opponent** sprite:

![The Opponent sprite.](images/opponent.png)

```blocks3
when I receive [start v]
set size to (25)%
set rotation style [left-right v]
hide // This prepares the sprite to clone itself without showing it
repeat (7)
    create clone of [myself v]
end
````

--- /task ---

--- task ---

Give each clone a random appearance and position:

![The Opponent sprite.](images/opponent.png)

```blocks3
when I start as a clone
switch costume to (pick random (1) to (13))
go to x:(pick random (-100) to (240)) y:(pick random (-180) to (180))
show
repeat until <(lives) = (0)>
    point towards (Player v) // Each clone will chase the player
    turn right (pick random (-70) to (70)) degrees
    move (2) steps
    if on edge, bounce
end
delete this clone
```

--- /task ---

--- task ---

**Test your code.** Click on the green flag and watch the opponents rush towards the player!

--- /task ---

--- task ---

Now, add this new code **inside** your `repeat until`{:class="block3control"}`lives`{:class="block3variables"}`=`{:class="block3operators"}`0` loop, so that if the opponents touch the green line, they are moved away:

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
    +if <touching color ( #00ff00)?> then
	change x by (100)
	change y by (pick random (-180) to (180)
    end
end
delete this clone
```

--- /task ---

--- task ---

**Test your code.** Click on the green flag and watch the opponents rush towards the player, but bounce off the green line.

--- /task ---

In the next step, you will make the player be able to tag opponents, and make the opponents be able to catch the player.

--- save ---
