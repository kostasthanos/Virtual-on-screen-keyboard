# Virtual on screen keyboard
Virtual Keyboard with color tracking using Python and OpenCV library.

## Main Idea
The main idea of this project is to display the keys of a keyboard on the screen and allow the user to select (write) a character when the desired color (or finger) is inside the rectangle which correspondes to a key.

## Settings for drawing the on-screen keyboard
### [1] Rectangle and Text settings
```python
width, height = 65, 65
dist = 15 # Distance between two consecutive rectangles

# Initial position of text in frame
start_x = int((video.shape[1] - (10*width + 9*dist))/2)
start_y = 50

# Text settings
font = cv2.FONT_HERSHEY_PLAIN  # Font
fontThickness = 4              # Font weight
fontScale = 4                  # Font scale
```
### [2] Strings containing the necessary characters
Define strings containing the necessary characters like numbers, letters, symbols and commands.
```python
# Set a string with letters, numbers and symbols
numbers = "1234567890" # String containing 10 numbers (0-9)
alphabet = "1234567890QWERTYUIOP:ASDFGHJKL?ZXCVBNM,.<->[_]"

# Strings used in basic-'command' buttons
symbol_strings = ["BACK", "DELETE", "ENTER", "Aa", "SPACE", "NUM2SYM"] 
```
Explanation of the 6 final alphabet symbols
| Symbol | Explanation |
|   ---  |     ---     |
|    <   | Delete one character (BACK) |
|    -   | Delete all (DELETE) |
|    >   | Newline character (ENTER) |
|    [   | Change between capitals/lowercase (Aa) |
|    _   | Leave one character empty (SPACE) |
|    ]   | Change between numbers/symbols (NUM2SYM) |

For the drawing of all the characters (numbers,letters and commands) see the functions *[draw_letters](https://github.com/kostasthanos/Virtual-on-screen-keyboard/blob/main/vkct.py)* and *[draw_extra_chars](https://github.com/kostasthanos/Virtual-on-screen-keyboard/blob/main/vkct.py)*.

<p align="center">
  <img width="500" height="300" src="Images/keyboard1.png">
</p>

## Extra black window containing the selected characters (output message)
```python
paper = np.zeros((250,1000,3), np.uint8)
cv2.namedWindow("Paper")
# Starting position of text in "Paper" frame
start_write_x = 5
start_write_y = 35
```

<p align="center">
  <img width="600" height="250" src="Images/Paper frame.png">
</p>

## Color settings and color-tracking
Define the lower and upper color for the color-tracking part
```python
lower_color = np.array([75, 169, 45], np.uint8)
upper_color = np.array([96, 255, 255], np.uint8)
```
Alternative someone can use trackbars window. See *[Hand Gestures](https://github.com/kostasthanos/Hand-Gestures-and-Finger-Counting)* for more details.
