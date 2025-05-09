## Opponent Mechanics
Make opponent clones that appear in random places and follow the player.

--- task ---

Import/draw your opponent sprite and set its rotation style

```scratchblocks
when I receive [start v]
set size to (25)%
set rotation style [left-right v]
hide
```

This prepares the base opponent sprite to be cloned.

--- /task ---

--- task ---

Test opponent visibility and setup

Broadcast “start”—sprite should hide and size correctly.

--- /task ---

--- task ---

Spawn clones

```scratchblocks
repeat (7)
    create clone of [myself v]
end
```

This spawns multiple opponents for the player to tag.

--- /task ---

--- task ---

Test clone spawning

Check that 7 hidden clones appear after “start.”

--- /task ---

--- task ---

Write clone start behaviour

```scratchblocks
when I start as a clone
switch costume to (pick random (1) to (13))
go to x:(pick random (-100) to (240)) y:(pick random (-180) to (180))
show
```

This gives each clone a random look and starting position.

--- /task ---

--- task ---

Test clone appearance and variety

Run and confirm costume and position are randomised.

--- /task ---

--- task ---

Add basic chase-AI movement

```scratchblocks
repeat until <(lives) = (0)>
    point towards [Player v]
    turn right (15) degrees
    move (2) steps
    if on edge, bounce
end
delete this clone
```

This lets opponents move towards the player with simple AI.

--- /task ---

--- task ---

Test opponent chasing and bounce behaviour

Watch clones follow the player and bounce at edges.

--- /task ---

--- save ---
