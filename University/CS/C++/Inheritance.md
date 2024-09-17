# Inheritance
#cs 


Inheritance is a key feature in OOP that allows you to create new [[Classes]] (derived classes) based off of existing classes (base classes). It allows for code reuse and to establish class relations.

The syntax for inheriting a class is as follows:

```c++
class Base {
public:
    void baseFunction() {
        // Code specific to the base class
    }
};

class Derived : public Base {
public:
    void derivedFunction() {
        // Code specific to the derived class
    }
};
```

The Derived class will have access to the base class's public and protected methods. 

The Base class cannot access the derived class's methods. 

```c++
int main() {
    Derived d;
    d.baseFunction();     // Accesses the base class function
    d.derivedFunction();  // Accesses the derived class function
}
```

### Virtual and Pure Virtual Methods

Derived classes can override the functionality of base class methods. 

A virtual method is declared by the keyword `virtual`, and is declared in a base class to indicate that it can be overridden in derived classes. 

The derived class's iteration of the method would contain the keyword `override` to ensure this.

```c++
class Base {
public:
    virtual void virtualFunction() {
        // Base class implementation
    }
};

class Derived : public Base {
public:
    void virtualFunction() override {
        // Derived class implementation
    }
};
```

A pure virtual method, on the other hand, is declared in the base class but does not provide an implementation. 

If a class contains **at least one** pure virtual methods, it is considered an abstract class. Abstract classes **cannot** be instanced. 

Pure virtual methods exist as **placeholders** for derived classes to override.

```c++
class AbstractBase {
public:
    virtual void pureVirtualMethod() = 0;  // Pure virtual function
};

class Derived : public AbstractBase {
public:
    void pureVirtualFunction() override {
        // Derived class implementation
    }
};
```

Since abstract classes cannot be instanced, they are used to set out the guidelines for derived classes. 

For example, a general Animal class would not be instanced, but its derived classes could be specific animals that can be instanced.

If a derived class does not overload all pure virtual functions, it too is considered abstract, and thus cannot be instanced.

### Object Slicing and Polymorphism

Object slicing occurs when a derived class is assigned/passed to a base class object, resulting in a loss of derived-specific information. 

This occurs because the base class object can only store base class information, so additional members and attributes get lost or 'sliced off'.

For example:

```c++
class Base{
public:
	virtual void print() const{
		cout << "base" << endl;
	}
};

class Derived : public Base{
public:
	void print() const override{
		cout << "derived" << endl;
	}
	void derivedonly(){
		cout << "derived" << endl;
	}
};

void print(const Base b){
	b.print();
}

int main(){
	Derived d;
	print(d); //Prints "base", as print() expects a base object
}
```

It is also possible to create objects of a derived class using the base class as a type.

```c++
int main(){
	Derived d;
	Base b = d;
	
	d.derivedonly(); //prints "derived"
	b.derivedonly(); //error
}
```

Be warned that objects instanced this way will not have access to derived class specific elements (methods, variables, etc.)

To achieve true polymorphism and be able to access derived class-specific members and behaviour, use pointers or references to the base class.

This allows you to assign a derived class object to a base class pointer or reference and invoke virtual functions dynamically.

Below is an example using pointers, although pass by reference can also be used:

```c++
void print(const Base* b){
	b->draw();
}

int main() {
	Derived d;
	print(&d); //prints "derived"
	
	Base b = d;
	print(&b); //prints "base"
}
```

Virtual functions and dynamic dispatch (runtime polymorphism) can be leveraged to access derived class specific behaviour, when necessary.

It's important to note that the base class should have at least one virtual function for dynamic dispatch to work correctly. 

Without a virtual function, the compiler will resolve the function calls based on the type of the pointer or reference, rather than the actual object type.

Also important, you cannot access derived-**exclusive** methods and variables (elements that aren't being overridden) when passed as main without typecasting back to the derived, although it is unlikely you would even need to do this. 

If necessary, either make the method available virtually in the base class or typecast the base object back to derived. 

### Access Modes

Although usually classes are inherited using the `public` keyword, `private` and `protected` can also be used.

`Public` - The members of the base class are inherited by the derived class just as they are.

`Private` - **All** the members of the base class become `private` members in the derived class.

`Protected` - The `public` members of the base class become protected members in the derived class.
 
