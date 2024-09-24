# Move Semantics & The Rule of Five
#cs 

## Rule of Five
The Rule of Five is a guideline that helps developers manage resources such as dynamic memory, file handles, or network connections within a class.

It dictates that if a class needs to explicitly define any of the following five special member functions, it likely needs to explicitly define all five:

- **Destructor**: Releases resources acquired by the object
- **Copy Constructor:** Creates a new object as a copy of an existing object
- **Copy Assignment Constructor:** Assigns contents of one object to another existing object
- Move Semantics Constructors
	- **Move Constructor**: Transfers resources from a temporary object (r-value) to an existing object
	- **Move Assignment Constructor**: Transfers resources from a temporary object (r-value) to an existing object


The rule of five ensures that resources are being managed correctly and consistently, preventing resource leaks, double deletions, and other issues relating to resource management.

### Destructor


Called when an object goes out of scope or explicitly deleted. 

Should free any resources allocated by the object.

```cpp
~Class()
{
	//Release resources, eg: delete[] ptr;
}
```

### Copy Constructor

Creates a new object as a copy of an existing object.

Called when an object is passed by value, returned by value, or explicitly copied.


```cpp
Class(const Class& other) 
{
    // Create a copy of other's resources
    ptr = new int[other.size];
    std::copy(other.ptr, other.ptr + other.size, ptr);
    size = other.size;
}
```



### Copy Assignment Constructor

Assigns the contents of one object to another existing object, handling self-assignment and releasing existing resources before copying.

```cpp
Class& operator=(const Class& other) 
{
    if (this != &other) {
        // Release existing resources
        delete[] ptr;
        // Copy other's resources
        ptr = new int[other.size];
        std::copy(other.ptr, other.ptr + other.size, ptr);
        size = other.size;
    }
    return *this;
}
```


### Move Constructor

Transfers resources from a temporary (r-value) object to a new object. 

Called when an object is initialised with a temporary object, enabling resource-efficient transfers.


```cpp
Class(Class&& other) noexcept 
{
    // Transfer resources from other to this object
    ptr = other.ptr;
    size = other.size;
    // Leave other in a safe state
    other.ptr = nullptr;
    other.size = 0;
}
```

### Move Assignment Constructor

Similar to the move constructor, but for assignment operations.

```cpp
Class& operator=(Class&& other) noexcept 
{
    if (this != &other) {
        // Release existing resources
        delete[] ptr;
        // Transfer resources from other to this object
        ptr = other.ptr;
        size = other.size;
        // Leave other in a safe state
        other.ptr = nullptr;
        other.size = 0;
    }
    return *this;
}
```

## Move Semantics

Move semantics are a feature in C++11 to enable efficient transfer of resources from one object to another. 

It revolves mainly around **Moving** instead of **Copying** the data, which is useful when working with larger objects or objects that manage resources.

The main advantages of move semantics are increased performance and more efficient resource management. This is because we are transferring rather than duplicating, which is more time and space efficient.

The key concepts include the two constructors mentioned previously as well as `std::move()` and r-values.


## R-values

R-value references allow the differentiation between temporary (r-value) and permanent (l-value) objects. An r-value reference is declared using `&&`

```cpp
void func(Class&& obj); // obj is an rvalue reference
void func2(Class& obj); //obj is an lvalue reference
```


## `std::move`

The `std::move` function is used to cast an object to an r-value reference, enabling move semantics. It doesn't actually move anything, it simply marks the object as eligible for moving.

```cpp
Class obj1;
Class obj2 = std::move(obj1); // obj2 is now the owner of obj1's resources
```

