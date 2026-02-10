# Custom Command Interpreter (C)

## Project Overview
This project is a custom implementation of a line-by-line script interpreter written in C. It demonstrates how to build a basic state machine that processes text commands, manages variable memory, and handles control flow logic without using external libraries.

I built this project to deepen my understanding of:
* **Low-Level Logic:** Managing program state and execution loops manually.
* **Memory Management:** Using structs to simulate a variable storage system.
* **String Parsing:** Tokenizing raw user input into executable instructions.

## Technical Implementation
The program simulates a "Fetch-Decode-Execute" cycle found in computer processors:

1.  **Memory Model:** Uses a `struct Variable` array to map variable names to integer values (Symbol Table logic).
2.  **Instruction Decoding:** Uses `strtok` to parse input lines and identify commands.
3.  **Control Flow:** Implements a `goback` command that modifies the loop index (`k`) to create repetition loops based on variable comparison.
4.  **Arithmetic Logic:** Performs addition and subtraction with upper/lower bound checks (0-99) to ensure data stability.

## Supported Commands
| Command | Usage | Description |
| :--- | :--- | :--- |
| `set` | `set x 10` | Creates a variable `x` with value 10. |
| `add` | `add x y` | Adds `y` to `x` (Clamped at 99). |
| `sub` | `sub x y` | Subtracts `y` from `x` (Clamped at 0). |
| `show` | `show x` | Prints the value of `x` to the console. |
| `goback` | `goback 2 x y` | Jumps back 2 lines if `x < y` (Loop mechanism). |
| `exit` | `exit` | Stops execution. |

## How to Run
**1. Compile the code:**
```bash
gcc command_interpreter.c -o interpreter
./interpreter

set count 0
set limit 5
add count 1
show count
goback 2 count limit
exit
