# Bitwise Shift Operators
#cs 

## Shift Operators

- The bitwise shift operators move the bit values of a binary object
- The left operand specifies the value to be shifted
- The right operand specifies the number of positions that the bits are to be shifted


Left Shift: x << y
- Shifts bit-vector x left by y positions
- Throws away extra bits on left
- Fill with 0s on the right

Right Shift: x >> y
- Shifts bit-vector x right by y positions
- Throws away extra bits on right
- Logical Shift:
	- Fill with 0s on the right
- Arithmetic Shift:
	- Replicate MSB on left


### Arithmetic vs Logical Shift

- Left Logical Shift — Each bit is shifted towards **left**, MSB is discarded and LSB becomes 0 
- Left Arithmetic Shift — Each bit is shifted towards **left**, MSB is discarded and LSB becomes 0, **hence similar to logical shift** 
- Right Logical Shift — Each bit is shifted towards **right**, LSB is discarded and MSB becomes 0 
- Right Arithmetic Shift — Each bit is shifted towards **right**, LSB is discarded and MSB becomes 1