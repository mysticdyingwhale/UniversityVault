# Basics
#cs 

## Basic Print

```c++
#include <iostream>
int main(){
	std::cout << "Hello World\n";
}
```

- `<<` is the output operator
	- **target** **stream** appears on the **left**
	- what is output is on the **right**
	- the brackets point towards the **output** stream

- `std::cout` represents the standard output 
- **string literals** are always surrounded by double quotes " "
- `#include` specifies a library for the compiler
- `iostream` provides the definition for `std::cout `(and much more)


```c++
#include <iostream>
using namespace std;

int main(){
	cout << "Hello World" << endl;
}
```

- `using namespace std;` allows for reference to `cout` and other symbols without typing out `std::`
- Best practice not to use
- Outputs can be chained 
	- `endl` - end of line character
		- full reference: `std::endl`
		- alternative to `\n`
		- flushes output stream


## Variables

```c++
#include <iostream>
#include <string>
using namespace std;

int main(){
	int age = 42;
	double pi = 3.14159;
	string txt = "the cat in the hat";
	char q = 'q';
	cout << "age: " << age << ", pi: " << pi << ", text: " << txt << endl;
}
```

- `#include string` because strings are not a primitive type
- characters are a separate type from `string`
	- character literals use single quotes `char Q = 'q'`


```c++
int main(){
	int age;
}
```

When declaring variables, ensure to provide an initial value as there is no guarantee of the value that will be returned.

Strings work differently and are initialised as an empty string automatically.


## Input

```c++
int main(){
	int i_var = -1;
	cout << "i_var: " << i_var << endl; //"i_var: -1"
	cout << "input an integer value: " ;
	cin >> i_var;
	cout << "i_var: " << i_var << endl; //"i_var: {user input}"
}
```

- `cin` is the standard input from a keyboard
- angle brackets point from stream to variable


## Vectors

```c++
#include <iostream>
#include <vector>
using namespace std;

int main(){
	vector<int> vec;
	cout << "vec.size(): " << vec.size() << endl; //0
	
	vec.push_back(17);
	vec.push_back(42);
	cout << "vec.size(): " << vec.size() << endl; //2
	
	for(size_t i = 0; i < vec.size(); ++i){
		cout << vec[i] << '';
	}
	
	cout << endl;
	vec.clear();
	
	cout << "vec.size(): " << vec.size() << endl;
}
```

- Available after `#include <vector>`
- full name is `std::vector<type>`
- Similar to Python List and Java ArrayList
- vectors are a generic type
- other useful methods:
	- `back()`
	- `pop_back()`
	- `capacity()`

### Ranged for loop

```c++
int main(){
	vector<int> vec;
	
	for(size_t i = 0; i < vec.size(); ++i){
		cout << vec[i] << '';
	}
	cout << endl;
	
	for (int value : vec){
		cout << value < '';
	}
	cout << endl;
}
```

- Both loops work the same
- ranged for is easier to use for vectors

## 2D vectors

```c++
int main(){
	const int ROWS = 10;
	const int COLS = 10;
	vector<vector<int>> mat;
	
	for(int row = 0; row < ROWS; ++row){
		mat.push_back(vector<int>(COLS));
		for (int col = 0; col < COLS; ++col){
			mat[row][col] = row * ROWS + col;
		}
	}
	
	for(int row = 0; row < ROWS; ++row){
		for (int col = 0; col < COLS; ++col){
			cout << mat[row][col] << '';
		}
		cout << endl;
	}
}
```

- filling a 2D matrix with values from 0 to 99
- constants are commonly in all caps
- vector is created and pushed onto mat

## String

```c++
#include <string>
#include <iostream>
using namespace std;

int main(){
	string str1 = "Twas brillig and";
	cout << str1 << endl; //"Twas brillig and"
	for (char ch : str1){
		cout << ch << '';
	}
	cout << endl; //"Twas brillig and"
	
	string str2 = "the slithy toves";
	string str3 = str1 + str2;
	cout << str3 << endl;  //"Twas brillig and the slithy toves"
}
```

- Available after `#include <string>`
- `string` literals use double quotes `string txt = "hello" ` 
- `string` variable acts like a `vector` of characters
	- `push_back()`, `pop_back()`, `size()`, `clear()`
- additional features
	- input/output from `string` is possible (not possible for `vector`)

- `strings` are **mutable**

```c++
int main(){
	string animal = "bat";
	
	animal[0] += 1;
	
	cout << animal << endl; //"cat"
}
```


## Functions

### Function Prototypes

- Functions must be declared before being used
- Using a function prototype declares a function
	- It informs the compiler that a definition will be provided later on

```c++
int factorial(int, char);

int main(){
	...
	factorial(5,'a');
	...
}
int factorial(int n, char i){
	...
	return ...
}
```

- Prototypes provide important information
	- return type
	- function name
	- function parameter type(s)


### No return type

- Functions do not have to return a value
- The return type can be indicated as `void` 

## Passing Arguments

### Pass by Value

Simply passing the value of the variable. Use for primitive types. Basically a copy.

The original variable will not be modified if the parameter is modified.

```c++
void func(int x){
	...
}
```

### Pass by Reference

Passing a reference to the variable, use for non primitive types.

The original variable is modified when the parameter is modified.

```c++
void func(string& y){
	...
}
```

##### Constant Reference

Passing a constant reference to the variable. The reference cannot be used to modify the original variable.

Read only reference.

```c++
void func(const string& y){
	...
}
```

### Pass by Pointer

Passing a pointer to the variable. The pointer is a variable that stores the address of another variable. To access the variable it points to, it must be dereferenced. 

```c++
int y = 3;
int* ptr = &y;

void func(int* ptr){
	cout << *ptr << endl; //outputs 3
	cout << ptr << endl; //outputs address of y, eg: 4r8x02
}
```

More on [[Pointers]]


