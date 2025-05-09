## Player Mechanics
Create the player, make it move with the keyboard, and add what happens if the player wins or loses.

--- task ---

**Import or draw the player**

Create or add a neutral-sized sprite for the player.  
This provides the main controllable sprite for the player.

--- /task ---

--- task ---

**Stage the “start” handler for the player**

```scratchblocks
when I receive [start v]
set size to (25)%
go to x:(-160) y:(0)
wait (1) seconds
```

This ensures the player begins in the correct position and scale.

--- /task ---

--- task ---

**Test player position and size**

Broadcast “start” and ensure correct placement and scaling.

--- /task ---

--- task ---

**Add arrow-key movement**

```scratchblocks
repeat until <(lives) = (0)>
    if <key [up arrow] pressed?> then change y by (10) end
    … (down/right/left) …
end
```

This allows the player to move around the stage using the keyboard.

--- /task ---

--- task ---

**Test player movement**

Press arrow keys—verify movement is smooth and accurate.

--- /task ---

--- task ---

**Add Kabaddi-timer reset**

```scratchblocks
if <key [space] pressed?> then
    play sound [kabaddi v]
    set [kabaddi v] to (1)
end
```

This resets the kabaddi countdown when the player calls out.

--- /task ---

--- task ---

**Test spacebar and kabaddi reset**

Press or hold space—check that `kabaddi` resets to 1.

--- /task ---

--- task ---

**Add “when I receive” handlers** for `tag player`, `win`, and `lose`

Reset player, play sounds, show messages, and stop movement.  
These events trigger key game outcomes and player responses.

--- /task ---

--- task ---

**Test player tag and endgame handlers**

Manually broadcast each message to verify correct response.

--- /task ---

--- save ---
