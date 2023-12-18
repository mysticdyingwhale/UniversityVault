#cs 

Floating point representation exists because we cannot represent every single decimal value with [[Floating Point Representation]].

>Floating point numbers are **more hardware intensive** to generate and use as the process of creating them is more elaborate than fixed point numbers.

# Mantissa and Exponent 
   
A typical floating point number would consist of 2 parts, the mantissa and the exponent, the sizes of which will be given to you in the exam.

Think of the mantissa and exponent as the 'standard form' of [[Binary Representation]]. Below is an example in denary.
![Mantissa | 300](https://bournetocode.com/projects/AQA_A_Theory/pages/img/FPF.png)


In the case above, in order to get the final number that the standard form represents, we shift the decimal point of the mantissa to the right by 6 places.

 - If the exponent is a positive number, we shift right, thus making the final number bigger than the mantissa. 
 
 - If it is a negative, we shift left, making it smaller.

Below is a 6 digit mantissa and 4 digit exponent. 

```
0 1 1 0 1 0 | 1 1 0 1
```

The mantissa is a positive number, as the twos compliment (sign) bit is 0, and the exponent is negative, indicating a left shift.

$$0.11010 \times 2^{-3} = 0.00011010 $$

$$\frac 1{16} + \frac 1{32} + \frac 1{128} = \frac {13}{128}$$

   

## IEEE 754 Standard

Provides a uniform standard for floating point arithmetic used by most (if not all) of current CPUs. 

Standard accounts for rounding, overflow, and underflow.


### Components

- Sign
	- Determine whether the sign bit is 1 or 0
	- 1 if negative, 0 if positive
- Exponent
	- An 8-bit (for single precision) field used to represent the exponent in a biased form
- Mantissa
	- A 23-bit (for single precision) field used to represent the precision of the number

#### Converting from denary to IEEE binary

Steps:
- Convert the number to binary
- Normalize the number such that it has a single `1` before the binary point             (`1.xxxxxx`)
- Calculate exponent
	- Based on the number of places the binary point moved
	- In IEEE 754, its stored in biased form, meaning its 127 + the number of places
	- Convert the result to an 8-bit binary value
- Determine Mantissa
	- The fractional part after the binary point (`xxxxxxxx`)



#### Converting from IEEE binary to denary

Steps:
- Identify the components
	- Sign bit (1 or 0)
	- Exponent (next 8 bits)
	- Mantissa (last 23 bits)
- Calculate exponent
	- Convert to decimal 
	- Subtract the bias ($2^7 - 1$ for single precision)
- Calculate Mantissa
	- Add a leading `1` to the beginning of the mantissa
	- Convert to decimal, treat as fraction (after point, 1/2, 1/4, etc...)
- Put together $(-1)^{\text{sign}} \times 1.\text{mantissa} \times 2^{\text{exponent}}$ 