#cs 

Functors (also known as function objects) are classes that behave like functions and can be customized to provide specific functionality.

They are instances of classes or structures that have overloaded the  `operator()`

Functors provide a way to encapsulate a callable entity, such as a function or [[Lambda Functions|lambda]] expression, into an object with a state.

This concept is closely linked to [[Function Pointers]], but with additional benefits. Functors can store internal state and maintain context between function calls, unlike function pointers.


### Example

```c++
class AddValue{
public:
	AddValue(int value) : init_value(value) {} //Initialisation List
	
	//functor which returns sum of init_value and integer parameter 
	int operator()(int num){
	return (num + init_value)
	}
	
private:
	int init_value;
};

int main(){
	//initialises an AddValue instance with init_value 5
	AddValue addFive(5); 
	
	//calls AddValue functor on addFive instance, returns 15
	int finalSum = addFive(10); 
}
```

