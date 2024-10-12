# Get Next Line

## Introduction
This project implements a function called `get_next_line` that reads a file, or input from a file descriptor, line by line. The goal was to build a robust and memory-efficient way to handle input streams, without using standard library functions like `fgets`. This function allows reading from a file descriptor one line at a time, regardless of the length of the line or the size of the buffer.

## What I Did
The core of this project is the implementation of `get_next_line`, which:
- Reads from a file descriptor and returns the next line each time it’s called.
- Handles both large and small inputs efficiently by using a buffer to store unread data between calls.
- Manages memory dynamically to avoid overflows or leaks, which is essential when dealing with unpredictable input lengths.

### Key Aspects of the Implementation:
1. **Buffer Handling**: I implemented a system where data is read in chunks of a predefined buffer size. Any leftover data after finding a newline is saved and used in the next function call, making sure no data is lost between calls.

2. **Dynamic Memory Management**: The function dynamically resizes the string as needed to accommodate lines of any length, ensuring there is no static size limit imposed on the input.

3. **Edge Case Handling**: A lot of attention was given to edge cases, such as:
   - Properly managing end-of-file conditions.
   - Handling empty lines, files with no newlines, or very large lines.
