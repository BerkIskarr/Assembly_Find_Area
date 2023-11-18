# Assembly_Find_Area
This assembly program calculates the area based on provided values for the radius and a constant, and then prints the result using the printf function.

## Description

The program performs the following steps:

1. Loads the radius value (`$s0`) into the XMM0 register.
2. Squares the radius by multiplying it by itself.
3. Multiplies the squared radius by the constant pi (`3.1415`).
4. Loads the value of `$s1` into the XMM1 register.
5. Loads the value `2.0` into the XMM2 register.
6. Multiplies the result by `2.0`.
7. Divides the result by the value in `$s1`.
8. Stores the calculated area in the `area` variable.

The calculated area is then printed using the printf function with the format string "Area is %f".

## Requirements

NASM (The Netwide Assembler)
GCC (GNU Compiler Collection)

## Contributing
Feel free to contribute to this project by submitting issues or pull requests. Follow the coding standards used in the existing code.
