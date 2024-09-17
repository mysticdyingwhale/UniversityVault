# Classes
#cs 

A class is a user-defined type that can be used as a blueprint for creating objects. 

Below is a basic outline of a class and what each element would typically contain:

```c++
class ClassName{
	//friend function
	friend ostream& operator << (ostream& os, const ClassName& classname){
		os << "value: " << value << endl;
		return os; 
	} 
	
public:
	//initialisation list
	ClassName(int somevalue) : value(somevalue), protval(false){}
	
	//setters and getters
	int getValue() {return value;}
	void setValue(int someValue) {value = someValue;}
	
	//publically accessable methods and variables
	void clearval(){
		value = 0;
		protval = false;
	}

private:
	//private variables
	int value;
	//can only be accessed outside of class by friend
protected:
	//protected variables and methods
	bool protval;
	//can only be accessed by friend and inherited classes
};
```

## Inheritance

[[Inheritance]] is a key feature in OOP that allows you to create new classes based off of existing classes. 

We refer to the new classes as 'derived' or 'child' classes, and the existing classes as 'base' or 'parent' classes.

## Copy Control

Copy control in C++ refers to the set of operations and mechanisms that govern how objects are copied or moved, assigned, and destroyed.

The four concepts it involves are:

- Copy Constructor
	- Initialises an object using another object of the same class
	- Invoked when a new object is being created as a copy of an existing object, such as during object initialization or when passing objects by value.
	- Typically performs a member-wise copy of the data members of the source object to the newly created object.

```c++
class MyClass{
private:
	int data;
public:
	MyClass(int d) : data(d) {}
	MyClass(const MyClass& rhs) : data(rhs.data) {} //copy constructor
};
```

- Copy Assignment Constructor
	- `operator=` is used to assign one object to another of the same class
	- Invoked when an already initialised object is assigned the value of another object
	- Typically performs a member-wise copy of the data members from the source object to the destination object.

```c++
class MyClass{
private:
	int data;
public:
	//Assignment Constructor
	MyClass& operator=(const MyClass& rhs){
	if(this != &rhs){
		data = rhs.data;
		}
		return *this;
	}
};
```
  
- Move Constructor and Move Assignment Operator
	- Allow the efficient transfer of resources (such as dynamically allocated memory) from one object to another without the need for unnecessary copying
	- Constructor invoked when a new object is being initialized by "moving" the resources from an existing object (typically an r-value).
	- Assignment operator is used to assign the resources from one object to another object.
	- Typically faster and more efficient than copying, as they involve transferring ownership rather than duplicating resources.

```c++
class MyClass {
private:
    int* data;
public:
    MyClass(int size) : data(new int[size]) {}

	//Move Constructor
    MyClass(MyClass&& rhs) noexcept : data(rhs.data) {
        rhs.data = nullptr;
    }
    
    //Move Assignment Operator
    MyClass& operator=(MyClass&& rhs) noexcept {
        if (this != &rhs) {
            delete[] data;
            data = rhs.data;
            rhs.data = nullptr;
        }
        return *this;
    }
};
```

- Destructor
	- A special member function that is automatically called when an object goes out of scope or is explicitly destroyed.
	- Responsible for cleaning up any resources (such as dynamically allocated memory or open file handles) held by the object before its memory is freed.
	- Invoked in the reverse order of object creation (i.e., last-in, first-out) for objects on the stack and in the order of dynamic memory allocation for objects on the heap.

```c++
class MyClass{
private:
	int* dynamicData;
public:
	MyClass(int d) : dynamicData(new int[10]) {}
	//Destructor
	~MyClass(){
		//releases the dynamically allocated memory when object is destroyed
		delete [] dynamicData;
	}
};
```


## Operator Overloading

Operator overloading allows you to redefine the behaviour of certain operators when applied to objects of user-defined classes or types. 

Operators such as (+, -, * , / , etc. ) can be overloaded to change functionality and improve code clarity.

When overloading as a member function:

```c++
class MyClass {
public:
    MyClass operator+=(const MyClass& other) {
        // Define the behavior of the addition operator for MyClass
        MyClass result;
        // Perform the addition and store the result in 'result'
        return result;
    }
};
```

When you should define as member function:
- When the left-hand side operand of the operator is an object of your class
- When the operation requires accessing the internal state or private members of the class
- EG: +=, -=, ++, --, == , <<, etc.

Some operators (=, +=, -=, `[]` , ( ) ) **must** be defined as member functions.

When overloading as a non-member function:

```c++
class MyClass {
    // ...
};

MyClass operator+(const MyClass& lhs, const MyClass& rhs) {
    // Define the behavior of the addition operator for MyClass
    MyClass result;
    // Perform the addition and store the result in 'result'
    return result;
}
```

When you should define as non-member function:
- When neither operand of the operator is an object of your class
- When the operation is symmetric, meaning it doesn't depend on the internal state of a particular object
- When working with different types, including built-in types and types from other libraries
- EG: +, -, * , /, !=, >> 

Allows you to overload operators for built-in types and user-defined types that you don't control.



Examples of overloadable operators:

![[Pasted image 20230615000007.png|300]]