#cs 
   

When dealing with a denary number we can represent a fraction of a number with a decimal place.



>[!note] 
>Take the number 4.5
This number is equivalent to 4 + $\frac1 2$




**We can do this in a similar way with [[Binary]].**

In fixed-point binary, numbers smaller than zero decrease with size $\frac 1 {2^n}$

Meaning you would write it like this:

`
8 4 2 1 0.5 0.25 0.125 0.0625
`

`
0 1 0 0.1 0 0 0
`

For a number like 3.6:

`
0 0 1 1.1 0 0 0
`

It is rounded down because there are limitations to the fixed point representation system. This is why [[Floating Point Representation]] exists.