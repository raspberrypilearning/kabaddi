## Stage Setup

Set up the game by drawing the green line and making all the variables you will need.

--- task ---

Paint the “green line”. This sets a safe zone for the player.

![](images/backdrop_menu_paint.png)

In the **Backdrops** editor, draw a vertical green line at somewhere around x = –100 (a bit to the left of the middle). It should be 20 pixels thick.

![ Editor showing a green vertical line drawn as a backdrop.](images/backdrop_editor.png)

--- /task ---

--- task ---

Create two variables: `lives`{:class='block3variables'} and `opponent tagged`{:class='block3variables'}

![Variable list showing “lives” and “opponent tagged” both ticked.](images/variables.png)

These variables will control scoring, and tell the game if the player has won or lost.

--- /task ---

--- task ---

Write the game “Start” script:

![Stage with a centred vertical green line.](images/stage.png)

```blocks3
when green flag clicked
set [lives v] to (5)
set [opponent tagged v] to (0)
```

--- /task ---

--- task ---

Create a new `broadcast`{:class='block3events'} called `start`, and add the broadcast block to the bottom of your script:

```blocks3
when green flag clicked
set [lives v] to (5)
set [opponent tagged v] to (0)
+broadcast (start v)
```

This is the message we will use to start all the other sprites in the game.

--- /task ---

Add the counters for both `lives`{:class='block3variables'} and `opponent tagged`{:class='block3variables'}, as these are the two variables that control winning and losing the game.

--- task ---

Create two new `broadcast`{:class='block3events'} messages called `win` and `lose`.

--- /task ---

--- task ---

Add this code to the bottom of your script:

![Stage with a centred vertical green line.](images/stage.png)

```blocks3
when green flag clicked
set [lives v] to (5)
set [opponent tagged v] to (0)
broadcast (start v)
+forever
if <(opponent tagged) = (7)> then // Tagging 7 opponents means you win.
    broadcast (win v)
    wait (3) seconds
end
+end
```

--- /task ---

--- task ---

Add the code for running out of lives. 

```blocks3
when green flag clicked
set [lives v] to (5) // The player has 5 lives to start
set [opponent tagged v] to (0)
broadcast (start v)
forever
if <(opponent tagged) = (7)> then
    broadcast (win v)
    wait (3) seconds
end
+if <(lives) = (0)> then
    broadcast (lose v)
    wait (3) seconds
+end
end
```

--- /task ---

In the next step, make the controls for your player!

--- save ---