#cs 

A lambda function is an anonymous function that can be defined inline, without the need for a separate function declaration. 

It allows you to create small, self-contained functions on the fly, often used for short-lived or one-time uses.


```c++
[capture-list](parameters) -> return-type 
{
    // Body of the lambda function
}
```

The return type can be explicitly declared using `-> return-type`, or it can be deduced automatically by the compiler if the lambda function's body has a single `return` statement.


## Capture List

The capture list specifies the variables captured from the enclosing scope. 

These variables can be accessed and used within the lambda function. 

The capture list is optional, and if not provided, the lambda function does not capture any variables. The capture list is specified within square brackets.

When you capture a variable, you make it available for the lambda to use even when the variable goes out of scope in the enclosing context.

Captured variables can be accessed and used within the lambda function's body as if they were local variables. 

The lambda can modify captured variables if they were captured by reference or using capture expressions with modification.


### Types

- By value: `[variable]` captures `variable` by value.
- By reference: `[&variable]` captures `variable` by reference.
- By value with copy: `[variable = value]` captures `variable` by value and initializes it with `value`.
- By reference with modification: `[&variable = value]` captures `variable` by reference and initializes it with `value`.
- Capture all variables by value: `[=]` captures all variables from the enclosing scope by value.
- Capture all variables by reference: `[&]` captures all variables from the enclosing scope by reference.


## Example

A basic example of a lambda function which squares a given number. 

No variable is captured.

```c++
#include <iostream>

int main() {
    int num = 5;
    auto square = [](int x) { return x * x; };

    std::cout << "Square of " << num << " is: " << square(num) << std::endl;
    return 0;
}

```