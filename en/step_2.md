## Stage Setup

Set up the game by drawing the green line and making all the variables you will need.

--- task ---

Paint the “green line”. This sets a safe zone for the player.

![](images/backdrop_menu_paint.png)

In the **Backdrops** editor, draw a vertical green line at x = –100. It should be 20 pixels thick.

![](images/backdrop_editor.png)

--- /task ---

--- task ---

Create two variables: `lives`{:class='block3variables'} and `opponent tagged`{:class='block3variables'}

![](images/variables.png)

These variables will control scoring, and tell the game if the player has won or lost.

--- /task ---

--- task ---

Write the game “Start” script:

![](images/stage.png)

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
+broadcast [start v]
```

This is the message we will use to start all the other sprites in the game.

--- /task ---

Add the counters for both `lives`{:class='block3variables'} and `opponent tagged`{:class='block3variables'}, as these are the two variables that control winning and losing the game.

--- task ---

Tagging 7 opponents means you win. Add this code to the bottom of your script:

![](images/stage.png)

```blocks3
when green flag clicked
set [lives v] to (5)
set [opponent tagged v] to (0)
broadcast [start v]
+forever
if <(opponent tagged) = (7)> then
    broadcast [win v]
    wait (3) seconds
end
+end
```

--- /task ---

--- task ---

Add the code for running out of lives. 

In this example, the player has 5 lives when the game starts:

```blocks3
when green flag clicked
set [lives v] to (5)
set [opponent tagged v] to (0)
broadcast [start v]
forever
if <(opponent tagged) = (7)> then
    broadcast [win v]
    wait (3) seconds
end
+if <(lives) = (0)> then
    broadcast [lose v]
    wait (3) seconds
+end
end
```

--- /task ---

In the next step, make the controls for your player!

--- save ---