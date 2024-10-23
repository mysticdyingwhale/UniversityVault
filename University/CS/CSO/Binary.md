# Binary
#cs 

## Basics


Everything on a computer is encoded as sets of bits.

Bits are used because it is easy to store bi-stable elements, and it is reliably transmitted over noisy and inaccurate wires.


The Binary system goes up in terms of powers of 2, which is essentially to say $2^n$.
- Most Significant Bit (MSB) : The bit in a binary number which is of the greatest numerical value.
- Least Significant Bit (LSB) : The bit in a binary number which is of the lowest numerical value.
-  If the LSB is 1, the number is odd. Other wise, it is even.
We can represent numbers with decimal points using [[Floating Point Representation]] and [[Floating Point Representation]] .


### Hexadecimal

Hexadecimal is Base 16, as opposed to Binary's base 2 and denary's base 10. 

The 16 symbols are: 0-9 + A, B, C, D, E, F

Hex is used as a shorthand for binary. 

Usual notation is: `0xFA1D37B` or `0xfa1d37b` (keep case consistent)

One hex digit holds 4 bits of information, making it very useful for representing binary in a more succinct manner.


### Two's Compliment

- To store a negative denary number in binary, you must use Two's complement.
- Two's complement is when you make the MSB a negative number. The value of the MSB will tell you if the number is positive or negative.
- If we're looking at the Two's complement, the MSB must be zero for the final value to be positive. Otherwise it is a negative number.
- To get the negative value of a positive decimal integer, invert it's equivalent binary integer value and apply Two's complement to the MSB. You then add one to the number to get the final answer.
- Two's compliment binary numbers are referred to as 'signed'


#### Example: 

To get from 5 to -5

```
8 4 2 1

0 1 0 1
```

1. Invert it and apply Two's Compliment to the MSB:

```
-8 4 2 1

 1 0 1 0
```

2. Which equals -6 in Denary. To get from -6 to -5, we must add one at the end
   
```
-8 4 2 1

 1 0 1 1
 ```

**Which gives us the final answer of -5.**



In C, an unsigned integer is noted by `u` suffix: `5u, 5245u`

Integers are signed by default in C.