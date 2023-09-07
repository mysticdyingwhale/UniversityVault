#cs 

A function pointer, put simply, is just a pointer to a function. It can be used when a set of code is to be kept unchanged, but may require different functions to be called within it.

Rather than rewriting the code for each different function, using a function pointer saves time keeps cleaner code.

### Syntax

The syntax for declaring a function pointer is:

`return_type (*funcptr)(parameter_type, ...)`

Referencing:

`funcptr = funcname`

Dereferencing:

`data_type x = *funcptr`

### Example

Below is an example use case for function pointers: 
```c++
#include <cstdio> //for printf

int multiply(int a, int b){
	return(a * b);
}

int addition(int a, int b){
	return(a + b);
}

void print(int (*operation)(int,int)){
	int a = 5;
	int b = 10;
	printf("The result of operation between %d and %d is %d\n",a,b,operation(a,b));
}

int main(){
	print(&multiply);
	print(&addition);
}
```

The print function is designed to take in any pointer to an operator function which operates on two integers as a parameter. 

In `main`, we call the print function using both `addition` and `multiply` function pointers as parameters.

