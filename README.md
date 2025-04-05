<<<<<<< HEAD
Project Overview
This project implements a custom version of the C printf function, called _printf, which handles various format specifiers. The goal is to replicate the functionality of the standard printf function, while ensuring it adheres to the constraints and requirements of the project.

Authors:
elshadyusifov

babakyusifov

Table of Contents
Description

Requirements

Installation

Usage

Supported Format Specifiers

File Structure

Examples

Man Page

License

Description
The _printf function is a simplified version of the standard printf function. It is designed to print formatted output to the standard output (stdout). This project handles specific format specifiers and returns the number of characters printed (excluding the null byte).

Supported Format Specifiers:
Basic specifiers:

%c – Prints a character.

%s – Prints a string.

%% – Prints a literal percent sign (%).

Integer specifiers:

%d – Prints a signed decimal integer.

%i – Prints a signed integer.

Requirements
Allowed editors: vi, vim, emacs

Compiler: gcc (Ubuntu 20.04 LTS), using the following flags:

-Wall -Werror -Wextra -pedantic -std=gnu89

File structure:

main.c: Example test file for testing the functionality of _printf.

main.h: Header file that contains the prototypes for _printf.

printf.c: The implementation of the _printf function.

Code Style
The code must follow the Betty style (for both C and documentation).

There should be no global variables used.

Each C file should contain no more than 5 functions.

Compilation
To compile the project, run:

bash
Copy
$ gcc -Wall -Wextra -Werror -pedantic -std=gnu89 -Wno-format *.c
Man Page
A manual page is available for the _printf function. It provides detailed information about its usage, format specifiers, and behavior.

Installation
To use this program:

Clone the repository:

bash
Copy
git clone https://github.com/elshadyusifov/holbertonschool-printf.git
Navigate to the project directory:

bash
Copy
cd holbertonschool-printf
Compile the files:

bash
Copy
gcc -Wall -Wextra -Werror -pedantic -std=gnu89 -Wno-format *.c
Usage
To test the _printf function, you can use the example main.c provided, or you can create your own test cases. Below is an example of how to call the _printf function:

c
Copy
#include "main.h"

int main(void)
{
    int len;
    int len2;
    unsigned int ui;
    void *addr;

    len = _printf("Let's try to printf a simple sentence.\n");
    len2 = printf("Let's try to printf a simple sentence.\n");

    _printf("Length:[%d, %i]\n", len, len);
    printf("Length:[%d, %i]\n", len2, len2);

    _printf("Negative:[%d]\n", -762534);
    printf("Negative:[%d]\n", -762534);

    return 0;
}
To execute:

bash
Copy
$ ./printf
This will output the formatted strings and return the length of the printed output.

Supported Format Specifiers
1. Basic Specifiers
%c – Prints a single character.
Example: _printf("%c", 'A'); prints A.

%s – Prints a string.
Example: _printf("%s", "Hello, world!"); prints Hello, world!.

%% – Prints a literal percent sign.
Example: _printf("100%%"); prints 100%.

2. Integer Specifiers
%d – Prints a signed decimal integer.
Example: _printf("%d", -42); prints -42.

%i – Prints a signed integer.
Example: _printf("%i", 10); prints 10.

File Structure
bash
Copy
.
├── main.c          # Example test file
├── main.h          # Header file with function prototypes
├── printf.c        # Implementation of the _printf function
├── man_3_printf    # Manual page for _printf
└── README.md       # Project description and instructions
main.h
Contains the prototype of the _printf function and any necessary includes.

c
Copy
#ifndef MAIN_H
#define MAIN_H

#include <stdarg.h>

int _printf(const char *format, ...);

#endif /* MAIN_H */
printf.c
Contains the implementation of the _printf function.

c
Copy
#include "main.h"
#include <unistd.h>
#include <stdarg.h>

/**
 * _printf - Custom printf implementation
 * @format: The format string
 * Return: The number of characters printed
 */
int _printf(const char *format, ...)
{
    va_list args;
    int count = 0;
    const char *ptr;

    va_start(args, format);

    for (ptr = format; *ptr != '\0'; ptr++)
    {
        if (*ptr == '%' && (*(ptr + 1) == 'c' || *(ptr + 1) == 's' || *(ptr + 1) == 'd' || *(ptr + 1) == 'i' || *(ptr + 1) == '%'))
        {
            ptr++;
            if (*ptr == 'c')
                count += write(1, va_arg(args, int *), 1);
            else if (*ptr == 's')
                count += write(1, va_arg(args, char *), strlen(va_arg(args, char *)));
            else if (*ptr == 'd' || *ptr == 'i')
                count += print_integer(va_arg(args, int));
            else if (*ptr == '%')
                count += write(1, "%", 1);
        }
        else
            count += write(1, ptr, 1);
    }

    va_end(args);
    return count;
}
Man Page
A manual page (man_3_printf) is included in the project and explains the syntax and usage of the _printf function.

To view the man page:

bash
Copy
man ./man_3_printf
License
This project is open-source and free to use, modify, and distribute. It follows the principles of the MIT License.
=======
# holbertonschool-printf
## hi C
>>>>>>> 367426cbcf62acf12f9819b1474c7882b1bb36cf
