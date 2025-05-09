## Opponent Mechanics  
Make opponent clones that appear in random places and follow the player.

--- task ---

Import  an opponent sprite. In this example, we’ll use the `Character 1` sprite:

![](images/sprite-choose.png)  
![](images/opponent.png)

--- /task ---

--- task ---

Rename this sprite `opponent`.

![](images/rename-opponent.png)

--- /task ---

--- task ---

Add a setup script for the opponent:

```blocks3
when I receive [start v]
set size to (25)%
set rotation style [left-right v]
hide
````

This prepares the base sprite to clone without showing it, and makes it the same size as the player.

--- /task ---

--- task ---

Click the green flag and make sure the opponent hides and sizes correctly.

--- /task ---

--- task ---

Spawn 7 opponent clones when the game starts:

```blocks3

when I receive [start v]
set size to (25)%
set rotation style [left-right v]
hide
+repeat (7)
+    create clone of [myself v]
+end
```

--- /task ---

--- task ---

Click the green flag: make sure that 7 clones are created.

--- /task ---

--- task ---

Add a clone start script that gives each clone a random look and location:

```blocks3
+when I start as a clone
+switch costume to (pick random (1) to (13)) // makes the clones look different
+go to x:(pick random (-100) to (240)) y:(pick random (-180) to (180)) // makes sure that the clones start on the right side of the line
+show
```

Each clone will start at a random location with a random costume.

--- /task ---

--- task ---

CLick the green flag and verify that clones spawn in different places and look different.

--- /task ---

--- task ---

Add simple chase movement for clones:

```blocks3
when I start as a clone
switch costume to (pick random (1) to (13))
go to x:(pick random (-100) to (240)) y:(pick random (-180) to (180))
show
+repeat until <(lives) = (0)> // until the player runs out of lives
+    point towards [Player v]
+    turn right (pick random (-70) to (70)) degrees //turn slightly away from player to make movement more random
+    move (2) steps // bigger number  = harder game
+    if on edge, bounce
+end
+delete this clone
```

This makes each clone chase the player until the game ends.

--- /task ---

--- task ---

Click the green flag and confirm that clones chase the player and bounce at the edges.

--- /task ---

--- save ---

```
```
