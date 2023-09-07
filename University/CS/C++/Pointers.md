#cs 

A pointer is a derived data type that stores the address of other variables. We can access and manipulate the data stored in that memory location using pointers. 

Pointers provide a way to dynamically allocate and deallocate memory, and they are often used for efficient memory management and accessing complex data structures.

## Declaring a pointer

```c++
int y = 3;
int* ptr = &y;
```

## Derefencing a pointer 

To access the variable being pointed to, the pointer variable must be derefenced. 

```c++
int y = 3;
int* ptr = &y;
cout << *ptr << endl; //outputs 3
cout << ptr << endl; //outputs address of y, eg: 4r8x02

someClass* pointer;
pointer->method(); //syntax for calling methods of a variable
```

## Keyword This

The `this` keyword has 2 use cases. When the local variable’s name is the same as member’s name, and when you need to return a reference to the calling object.

When the local variable’s name is the same as member’s name:
```c++
class Test
{
private:
   int x;
public:
   void setX (int x)
   {
       // The 'this' pointer is used to retrieve the object's x
       // hidden by the local variable 'x'
       this->x = x;
   }
   void print() { cout << "x = " << x << endl; }
};
```


When you need to return a reference to the calling object
```c++
/* Reference to the calling object can be returned */ 
Test& Test::func ()
{
   // Some processing
   return *this;
} 
```


## The Heap

The stack is where variables declared inside a function will be stored.

The heap, on the other hand, is unused memory of the program and can be used to allocate the memory dynamically when program runs.

We can allocate memory dynamically onto the heap for any data type using the keyword `new`.

```c++
dataType* ptr = new dataType;
```

Once we are done using an object, we can free up the memory it takes up on the heap using the keyword `delete`.

```c++
delete ptr; // delete memory pointed to by ptr
delete [] ptr; // delete array pointed to by ptr 
```

Avoid calling delete on the same address more than once, unless the address is null. 

A pointer that used to point to something valid but doesn't anymore is normally referred to as a **dangling pointer**. These pointers should be set to null.

## Double Pointers

A pointer that points to another pointer can be defined in C++. Refer to it as a 'pointer to a pointer'

```c++
int a = 1;
int* b = &a;
int** x = &b;

//Dereferencing
cout << x << endl; //outputs address of b
cout << *x << endl; //outputs address of a
cout << **x << endl; //outputs 1
```

### Dynamic Array of Pointers

A dynamic array of pointers is an array which consists of variables of the pointer type. Those variables can point to other array elements. 

```c++
	int* p = new int[3]; //p[0], p[1], and p[2] can point to int variables
	
```

![[Pasted image 20230612015216.png|300]]

Pointer Arithmetic Syntax:
```c++
cout << p; //output 1000 (address of p)
cout << *p; //output 23 (p[0])
cout << *(p+1)  //output 38 (p[1])
cout << *(p) + 1 // output 24 (p[0] + 1)
```


A 2-dimensional dynamic array can also be achieved.

![[Pasted image 20230612015541.png|400]]

This is done by creating a 1-dimensional array of pointers, each of which pointing to their own 1-dimensional array of pointers. 
```c++
    // Creating the array of pointers
    // of size N
    int** p = new int*[N];
    int x = 1;
 
    // For multiplying
    for (int i = 0; i < N; i++) {
 
        p[i] = new int[N];
 
        // Creating N sized int memory
        // block
        for (int j = 0; j < N; j++, x++) {
 
            p[i][j] = 10 * x;
 
            // The above statement can
            // also be written as:
            // *(*(p+i)+j) = 10 * x
        }
    }
```


