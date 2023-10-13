# Welcome to the Vim CloudLunch 👋

## General Reminder
* Don't use your mouse - EVERYTHING is meant to be used through the keyboard

## Normal Mode - Basic Navigation - hjkl

Navigate the curser using the hjkl keys.

        ^
        k
        |
 < h  --+-- l >
        |
        j
        v

Hint: _You can use the arrow keys as backup_

## Navigation Playground - Simple Markdown table

| x |   |   |
|---|---|---|
|   | x |   |
|   |   | x |

## Navigating to specific lines - $Number + G

Line numbers are turned on through the VIM configuration file `.vimrc`: `set number`.

```
$Number + G - Jump to line $Number, e.g. 10G -> Jump to line 10
```

The number will be shown in the bottom right of the VIM status bar.

## Navigating the current line - 0 and $

This is a very long line that we want to skip to the end, and since we are smart consultants, we will not use the h and l keys for that, but instead use $. 
For jumping back to the beginning of the line, use 0.

## Navigating the current line - f & F

This is another very long line that we want to navigate, and since we are even smarter consultants, we will the f and F motions for that, followed by the character we want to jump to.
Example: 
* f followed by a jumps to the next occurence of the a character in the same line.
* F followed by a jumps to the previous  occurence of the a character in the same line.

## Navigating the current line - w, W, b, B, e & E

* w jumps to the start of next word 
* W jumps to the start of next WORD 
* b jumps to the start of the current or previous word 
* B jumps to the start of the current or previous WORD 
* e jumps to the end of the current or next word
* E jumps to the end of the current or next WORD

> _word_ -  A word consists of a sequence of letters, digits and underscores, separated with white space 
> _WORD_ - A WORD consists of a sequence of non-blank characters, separated with white space


Examples: 
This is another very long line that we want to navigate, we will use the w, W, b, B, e and E motions for that.
A long URL: www.thisisaverylongdomainname.com/these/are/considered/individual/words?separater=by?special=characters to test the different VIM motions.

```
> 92.1.168.43;hello_world&this_is_a_test is considered as a single WORD, but has multiple words

> load_data(
        url="https://drive.google.com/uc?id=1jI1cmxqnwsmC-vbl8dNY6b4aNBtBbKy3",
        output="Twitter.zip", second_parameter=True, third_parameter=False,
        path_train="Data/train/en",
        path_test="Data/test/en",
    )
``` 

## Navigating the current line - Repeating Motions

We can repeat any motion by pre-pending it with a number indicating _how_ many times we want to perform the motion.

Examples: 
* 3j performs the j command 3 times
* 4w performs the w command 4 times

This is another very long line that we want to navigate, and this time, we'll using the repeat motion by prepending the motion we want to perform by the number of how many times we want to perform it.

## Navigation - Jumping to matching paranthesis

With the % character, we can jump between matching paranthesis, e.g. (), [] and {}

Examples:

```
# In the same line: 
dummyFunction(argument1: str, argument2: int) -> None:
dummyFunction(argument1: str, argument2: int, ()) -> None:

# Across multiple lines

load_data(
	url="https://drive.google.com/uc?id=1jI1cmxqnwsmC-vbl8dNY6b4aNBtBbKy3",
	output="Twitter.zip", second_parameter=True, third_parameter=False,
	path_train="Data/train/en",
	path_test="Data/test/en",
	test=function()
)
```

## Editing Text - Insert Mode

Use i to switch to the insert mode to add some text at the position of the current cursor.
Use I to switch to the insert mode to add some text at the beginning of the current line.

Use <Esc> or <Ctrl> + C for swichting back to normal mode.

>   

Use a to append text at the next position of the cursor.
Use A to bring the cursor to the end of the line and append text at the next position of the cursor.

>

## Editing Text - Undo and Redo

In normal mode, you can use u to undo the previous actions and <Ctrl> + R to redo.

Try it out by changing some text in the insert mode, switching to normal mode via <Esc> and then using the undo and redo commands.


## Editing Text - Deleting Characters

Use x to delete the character at the current position.

Delete the *x* in this line.

You can combine this motion with a number to delete multiple characters, e.g. 5x.

## Editing Text - Deleting line

Use dd to delete the whole line at once:

DELETE ME.
DELTE ME AS WELL.


_Advanced Usage_: Use p to paste the previously deleted line somewhere else.

## Editing Text - Advanced Usage by changing or deleting within special characters

You can combine some of the previous motions and commands to execute powerful actions, e.g. to change or delete all text within certain characters.

Usage:
* d$ - Deletes anything until the end of the line
* d4w - Deletes anything until the end of the line
* Use ci" (think: change in <something>) to change the text within quotes
* Use di" (think: delete in <something>) to delete the text within quotes

Example:
* Change the text within those quotes "CHANGE ME by navigating into the quotes and executing the command above"
* Delete the text within those quotes "DELETE ME by navigating into the quotes and executing the command above"

## Normal Mode - Search and Replace

You can search for a specific term by pressing / and the entering the term.

Afterwards, you can jump between each occurrence with n for the next occurrence and N for the previous occurrence.

Enter the following command to search all occurrences of foo and replace them with bar.
The g in the end is the modifier for global.

:%s/foo/bar/g

## Command Mode - Saving a file and quitting Vim

Enter the command mode by pressing : which will cause the curser to appear in the bottom left of the status bar.

Enter :w for writing the file.
With :ws, you write the file and quite Vim afterwards. 

There are some shortcuts to save a file and quit Vim.
From the command mode, enter:
* ZZ
* :x

## Visual Mode - Perform actions on a selection

From normal mode, press v to enter the visual mode and use movements to expand the selection.
Afterwards, press the action of choice to perform on the selection, e.g. d to delete and p to paste somewhere else.

## Easter Eggs
:help holy-grail
:help 42

## Advanced Usage - Makros

A makro can be used to repeate a pre-recorded sequence of commands.

1. Press qq to start recording a makro.
2. Peform your sequence of actions of choice
3. Press q again to stop recording of the macro
4. Press @q to apply the makro again. You can also press 100@q to perform the action 100 times.

Example: remove a column from a csv file and also append a new, static column in the end

a1,a2,a3
bb1,bb2,bb3
ccc1,ccc2,ccc3
dddd1,dddd2,dddd3


## Python Code Example - For Playing around with "real" code

```
class Person:
    def __init__(self, name, age):
      self.name = name
      self.age = age

    def __str__(self):
        return f"{self.name}({self.age})"

    def greeting(name: str) -> str:
        return f"Hello {name}, my name is {self.name}"
```

## Advanced concepts

* Makros
* Replace-Mode - R - For replacing Text

## Reference

### Reminder - Vim Modes 
* Normal - For Navigation (Default)
* Insert - For Changing
* Command - For commands (saving, quiting, search, ...)
* Visual - For Selection
