---------- HOW TO PLAY ----------

----- TERMINOLOGY -----

- Btn cursor     (Shortening of "Button cursor") Cursor in main menu,
                 used to navigate between individual buttons.
- Input cursor   Cursor in main menu,
                 used to navigate between individual characters/digits within an input field.
- Tick           One forced movement downward.
                     By default, this is 1 per second, becoming faster as the game goes on.

- Lock-delay     Amount of time it takes for a falling piece to be frozen.

----- MENU CONTROLS -----

-    UP          If outside an input field, move button cursor up
-  DOWN          If outside an input field, move button cursor down
- RIGHT          If inside an input field, move input cursor right
-  LEFT          If inside an input field, move input cursor left

- ENTER          Select/deselect a button

- CTRL+D         Alternative to delete characters from a text input field
                 if backspace doesn't work

----- GAMEPLAY CONTROLS -----

-  DOWN/S        Move current piece down.
- RIGHT/D        Move current piece right.
-  LEFT/A        Move current piece left.

- X/N/UP/W       Rotate 90 degrees clockwise (right).
-    Y/Z/B       Rotate 90 degrees counter-clockwise (left).

- C/M            Hold or swap to a held piece.

  If there is no held piece, the current piece is stored and the next one grabbed.
  If there is a held piece, the current piece is swapped with the held piece.
  In both cases, the position of the current piece is reset to the top of the arena.

                     There can only be one swap/hold per round (until the current piece is frozen).

----- OTHER CONTROLS -----

-  SPACE         Pause/Resume the game if not in main menu.
- CTRL+R         Restart the game if not in main menu.
                     This does not reset anything input within the main menu.
- CTRL+H         Print this text.
                     Press again to hide this text.
- ESC            Go to main menu.
----- MECHANICS -----

- Every tick, the current piece falls by 1 tile.
  When it reaches the ground,
  it remains movable for the duration of the lock-delay before being frozen. When a piece is frozen,
  a new one spawns in its place, which can be seen from the next-piece display.

  If the piece is rotated into a position which is higher than the ground,
  the piece won't be frozen until reaching the ground again and the lock-delay passing.

- If a piece is frozen and it fills one or multiple lines, those lines are cleared,
  and everything above them falls down by the number of lines that were cleared.
  Every 10 cleared lines, there is a level-up, which increases the speed at which a piece falls.

- Every piece frozen is worth 50 score.

  The amount of score gained from line clears is based on the formula:
  (CLEARED ^ 2) * 100 * (1 + 0.075 * LEVEL),
  where CLEARED is the number of lines that were just cleared, and LEVEL is the current level.
  The score is always rounded down to the nearest integer.

  This means possible line-clears are worth the following:
  1 Line:   100-> 107-> 115...;
  2 Lines:  400-> 430-> 460...;
  3 Lines:  900-> 967->1035...;
  4 Lines: 1600->1720->1840....

  The amount of score gained from level-ups is based on the formula:
  200 * LEVEL, where LEVEL is the current level AFTER advancing.

  This means the first few level-ups are worth the following:
  0->1: 200;
  1->2: 400;
  2->3: 600.

  All three of these sources of score can happen within a single tick.

- If a piece spawns in and immediately overlaps any frozen piece, the game ends.
