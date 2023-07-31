# PROJECT: 0x07. C - Even more pointers, arrays and strings

## Project By: Jordan Crossley

## Course: ALX SOFTWARE ENGINEERING

![image](https://media.geeksforgeeks.org/wp-content/uploads/20230412184146/Strings-in-C.webp)

### A String in C programming is a sequence of characters terminated with a null character ‘\0’. The C String is stored as an array of characters. The difference between a character array and a C string is the string is terminated with a unique character ‘\0’.


### File: `0-memset.c` is a function that fills memory with a constant byte.

### File: `1-memcpy.c` is a function that copies memory area.

### File: `2-strchr.c` is a function that locates a character in a string.

### File: `3-strspn.c` is a function that gets the length of a prefix substring.

### File: `4-strpbrk.c` is a function that searches a string for any of a set of bytes.

### File: `5-strstr.c` is a function that locates a substring.

### File: `7-print_chessboard.c` is a function that prints the chessboard.

### File: `8-print_diagsums.c` is a function that prints the sum of the two diagonals of a square matrix of integers.

### File `100-set_string.c` is a function that sets the value of a pointer to a char.

### File `main.h` is the header file with the functions prototypes.

### File `_putchar.c` is the file that contains the _putchar function.

## File: 101-crackme_password contains the password for the [crackme2](https://github.com/holbertonschool/0x06.c) executable.
- You may need to install the `openssl` library to run the crakme2 program: `sudo apt install libssl-dev`
- Edit the source list `sudo vim /etc/apt/sources.list` to add the following line: `deb http://security.ubuntu.com/ubuntu xenial-security main` Then `sudo apt update` and `sudo apt install libssl1.0.0`

OR 

## The Advanced task no. 9
1. open the file using `vi -b 101-crackme_password`
2. when you see the vi window, don't use the insert mode, just type `:set binary` and hit enter
3. type `:set noeol` and hit enter
4. use the insert mode(i) and type abc123
5. esc `:wq` hit enter

==> Then do the github steps on Git add . , Git Commit -m "latest", git push
