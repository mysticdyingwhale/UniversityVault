#cs 

## 1-D Arrays

Given `T A[L]`:
- An array of data type T and length L  
- Contiguously allocated region of L * `sizeof(T)` bytes in memory:

![[Pasted image 20231217235707.png]]

To access an array:

Syntax: `displacement(base_register, index_register, scale_factor)`


EG: 
```perl
#%rbx = int arr[]
#%rcx = 2
movq $3 , (%rbx, %rcx, 8) #arr[2] = 3;
```