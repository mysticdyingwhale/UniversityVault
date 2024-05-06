# Smart Pointers
#cs 

Raw [[Pointers]] in C++ have many problems. If not handled properly they can lead to memory leaks, become dangling pointers or wild pointers, lead to buffer overflow or cause data inconsistency. 

Languages like Java and C# have introduced their own garbage collection mechanisms to smartly deallocate unused memory, ensuring that the programmer not have to worry about memory leaks.

To this end, C++ has introduced Smart Pointers, where when an object has been destroyed, the allocated memory is freed up as well.


Although it is possible to make your own smart pointer template, C++ provides several implementations.

To include smart pointers:

`#include <memory>`

The following explanations will use the Rectangle class:

```c++
class Rectangle {
    int length;
    int breadth;
 
public:
    Rectangle(int l, int b)
    {
        length = l;
        breadth = b;
    }
 
    int area() { return length * breadth; }
};
```

A Rectangle object will be instanced, and the pointers P1 and P2 will point to that object instance.
## `Unique_ptr`

`unique_ptr` stores one pointer only. We can assign a different object by removing the current object from the pointer.

Use `unique_ptr` when you want to have single, exclusive ownership of the object. Only one `unique_ptr` can point to one object.

Here  the `unique_pointer` is pointing to P1, but then we remove P1 and assign P2 so the pointer now points to P2:
```c++
 
int main()
{
// --\/ Smart Pointer
    unique_ptr<Rectangle> P1 = make_unique<Rectangle>(10,5);
    cout << P1->area() << endl; // This'll print 50
 
    // unique_ptr<Rectangle> P2(P1);
    unique_ptr<Rectangle> P2 = move(P1);
 
    // This'll print 50
    cout << P2->area() << endl;
 
    // cout<<P1->area()<<endl;
    return 0;
}
```

## `Shared_ptr`

`shared_ptr` allows more than one pointer to point to an object. A reference counter is maintained using the `use_count()` method. It is a container for raw pointers.

The reference counter is incremented each time a new pointer points to the object and decremented when the destructor of the object is called. 

Use `shared_ptr` when you want to assign a raw pointer to multiple owners



```c++
int main()
{
    //---\/ Smart Pointer
    shared_ptr<Rectangle> P1 = make_shared<Rectangle>(10,5);
    
    // This'll print 50
    cout << P1->area() << endl;

	//Declaring new shared_ptr using copy constructor
    shared_ptr<Rectangle> P2 = P1;
 
    // This'll print 50
    cout << P2->area() << endl;

    // This'll print 2 as Reference Counter is 2
    cout << P1.use_count() << endl;
    return 0;
}
```

## `Weak_ptr`

`weak_ptr` is similar to `shared_ptr`, however it does not maintain a reference counter. 

A `weak_ptr` is a copy of a `shared_ptr` that is owned by one or more of the `shared_ptr` instances, but is not involved in reference counting. It has no effect on the `shared_ptr` or its copies, even when deleted. 

In some cases, it may be required to break circular referencing between `shared_ptr` instances.

For example, given two classes A and B which both contain pointers to each other, A will point to B and B will point to A, meaning `use_count` will never reach zero and the pointers will never be deleted. 

This is why `weak_ptr` is used, as it is not reference counted. In the class where `weak_ptr` is declared, ownership is no longer shared, but they can still have access to the object.

![[Pasted image 20230612024502.png]]


```c++
int main()
{
    //---\/ Smart Pointer
    shared_ptr<Rectangle> P1 = make_shared<Rectangle>(5,10);

    // This'll print 50
    cout << P1->area() << endl;

	//Declaring weak_ptr using shared_ptr copy constructor
    weak_ptr<Rectangle> P2 = P1;    // P2 = P1;

    // This will not run, as you cannot operate on a weak_ptr
    cout << P2->area() << endl;

    // This'll print 1 as Reference Counter is 1
    cout << P1.use_count() << endl;
    return 0;
}
```