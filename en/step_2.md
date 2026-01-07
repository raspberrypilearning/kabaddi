## Set up the Stage

To set up the game, you will draw the green line and make all the variables you will need.

--- task ---

First, paint the green line. This will set a safe zone for the player.

![The 'Paint' option highlighted in the 'Choose a Backdrop' menu.](images/backdrop_menu_paint.png)

In the **Backdrops** editor, draw a vertical green line across the canvas at around x = –100 (between the left edge and the centre). The line should have a thickness of 20 pixels.

![The Backdrops editor with a green vertical line drawn across the canvas on the left-hand side.](images/backdrop_editor.png)

--- /task ---

--- task ---

Create two variables, `lives`{:class='block3variables'} and `opponent tagged`{:class='block3variables'}.

![The 'Variables' blocks menu with 'lives' and 'opponent tagged' ticked.](images/variables.png)

These variables will control scoring, and they will be used to identify when the player has won or lost.

--- /task ---

--- task ---

Write the game 'start' script:

![The Stage with a vertical green line across the centre.](images/stage.png)

```blocks3
when green flag clicked
set [lives v] to (5)
set [opponent tagged v] to (0)
```

--- /task ---

--- task ---

Create a new `broadcast`{:class='block3events'} with the message `start`, and add the `broadcast`{:class='block3events'} block to the bottom of your script:

```blocks3
when green flag clicked
set [lives v] to (5)
set [opponent tagged v] to (0)
+broadcast (start v)
```

This is the message that you will use to start all the sprites in the game.

--- /task ---

Next, add the counters for both `lives`{:class='block3variables'} and `opponent tagged`{:class='block3variables'}, to control winning and losing the game.

--- task ---

Create two new `broadcast`{:class='block3events'} messages, `win` and `lose`.

--- /task ---

--- task ---

Add this code to the bottom of your script:

![The Stage with a vertical green line across the centre.](images/stage.png)

```blocks3
when green flag clicked
set [lives v] to (5)
set [opponent tagged v] to (0)
broadcast (start v)
+forever
if <(opponent tagged) = (7)> then // Tagging 7 opponents means the player wins
    broadcast (win v)
    wait (3) seconds
end
+end
```

--- /task ---

--- task ---

Add the code for running out of lives:

```blocks3
when green flag clicked
set [lives v] to (5) // The player has 5 lives at the start
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

In the next step, you will make the controls for the player.

--- save ---