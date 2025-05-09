## Interactions & Game Logic
Add the rules for tagging, counting points, losing lives, and running the kabaddi timer.

--- task ---

Add Player–Opponent collision detection

```scratchblocks
// In Player’s loop:
if <touching [Opponent v]?> then
    play sound [pop v]
    broadcast [tag opponent v]

// In Opponent’s clone script:
if <touching [Player v]?> then
    change [touching v] by (1)
    wait until <not <touching [Player v]?>> 
    change [touching v] by (-1)
```

This handles when the player tags or is touched by an opponent.

--- /task ---

--- task ---

Test tag-on-touch logic

Bump into a clone—check sound and variable update.

--- /task ---

--- task ---

Add stage tag handlers

```scratchblocks
when I receive [tag opponent v]
change [opponent tagged v] by (1)

when I receive [tag player v]
change [player tagged v] by (1)
change [lives v] by (-1)
```

This updates the score and player lives after each tag.

--- /task ---

--- task ---

Test variable change on tag broadcasts

Manually broadcast and verify values increment/decrement.

--- /task ---

--- task ---

Add win/lose detection logic

```scratchblocks
forever
    if <(opponent tagged) = (7)> then broadcast [win v] end
    if <(lives) = (0)> then broadcast [lose v] end
end
```

This triggers end conditions when win or loss criteria are met.

--- /task ---

--- task ---

Test win/lose conditions

Manually set values to trigger win or lose.

--- /task ---

--- task ---

Implement kabaddi counter

```scratchblocks
when I receive [kabaddi v]
set [kabaddi v] to (1)
repeat until <(kabaddi) < (0)>
    broadcast [tag player v]
    broadcast [kabaddi v]
end
```

This countdown loop triggers a penalty if the player doesn’t reset it.

--- /task ---

--- task ---

Test kabaddi timer

Let timer expire to trigger tag. Press space to reset and test again.

--- /task ---

--- save ---
