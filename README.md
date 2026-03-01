# Description
Terminal-based puzzle game where you push a semicolon through code-filled grids, executing if-statements, loops, teleports, and more to solve unlockable levels.

Inspired by Baba Is You, this game reimagines its rule-bending mechanics in a coding twist: move your semicolon (;) to manipulate executable code blocks on the board. As you push strings and trigger the interpret process, commands like print, drop, scramble, variable assignments (a=1), and control structures dynamically alter the level—letting you rewrite logic to reach the goal and unlock the next challenge. Features undo/redo, predictive movement, and syntax-highlighted rendering in your terminal.

# Controls
Press arrow keys to move **all semicolons (;)** on the board in that direction simultaneously.

Strings can generally be **pushed**.  
However, pushing is **not possible** in these cases:
1. If any part of the string would go **off the board** when pushed
2. If the string being pushed **contains #**

Pressing an arrow key **triggers the interpret process** each time.

# Interpret
**Interpret** is the process of executing **executable code** currently present on the board.

## Code Execution Rules
Code is read **sequentially from top-left to bottom-right**, like reading a book.  
When a **semicolon (;)** is encountered, the **word immediately before it** is executed.  
Here, a "**word**" means a string **not containing spaces, #, or ;**.

### Execution Method
If an **executable string** exists, it is passed to `command_parser`.  
`command_parser` checks if the string is a **valid command** and, if so, **parses it** and passes it to `command_executer`.  
`command_executer` **actually executes** the command to manipulate the board.

If the string **cannot be executed**, no error occurs—it's simply **ignored** as non-code.

# Basic Syntax

## Assignment Operators and `get_value`
**Characters are treated as variables** by default.  
**Examples:**

print('a'); → prints "a"
a=1; print(a); → prints "1"

(`print` is a **function defined within the game**)

`**get_value**` is a function that **returns the value** of a specific string (not a game function, but code-level).  
**Examples:**

get_value(1) → 1
get_value(1+1) → 2
get_value(1==1) → true
get_value(a+1) → 3 (if a=2)


## if and while
`**if**` and **`while`** only affect code that appears on the **same line** after the condition statement.

