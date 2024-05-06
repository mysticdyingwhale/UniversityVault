# Templates
#cs 

Templates allow for generic code that can work with many data types/classes, similar to [[Function Pointers]]. 

They enable for code to be applicable to different classes and data types without having to rewrite the code for each specific type.

Templates are used extensively in the [[STL|Standard Template Library]]. 

### Syntax

To declare a template, insert the following line before the code you want to make a template:

`template<typename T>`

Here `T` represents the general type, with the keyword `typename` declaring it to be the type parameter.

### Example

The below example is a simple template function which compares the size of two variables. 
```c++
template<typename T>
T maxVal(T x, T y){
	return (x>y) ? x: y; // this is short for if x>y return x else return y
}

int main(){
	int x = 5;
	int y = 2;
	cout << maxVal(x,y); // 5
	
	char a = 'a';
	char h = 'h';
	cout << maxVal(a,h); // h
}
```

This would only work for types which have the > operator defined/overloaded. 

## Class Templates

Templates can also be made for [[Classes]], allowing for generic classes to be made. 

Below is an example of a generic class called Pair which takes in two different parameters on initialisation:

```c++
template<typename T1, typename T2>
class Pair{
public:
	T1 first;
	T2 second;
	
	Pair(const T1& a, const T2& b) : first(a), second(b) {}
};


int main(){
    Pair<int, double> p1(5, 3.14);
    Pair<std::string, bool> p2("Hello", true);
}
```

