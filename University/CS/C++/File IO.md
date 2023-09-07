#cs 

[[Basics of C++|C++]] maintains an extensive and easy to use file I/O system. 

To access file I/O:

`#include <fstream>`

### Basic Example

Below is a basic File I/O example involving opening a file named jabberwocky, storing the first word in the file into a string named 'something', and finally outputting that word.
```c++
#include <fstream>
#include <iostream>
#include <string>
using namespace std;

int main(){
	ifstream jab("jabberwocky");
	if (!jab){
		cerr << "failed to open jabberwocky";
		exit(1);
	}
	
	string something;
	jab >> something;
	cout << something << endl; //"first word of file"
	jab.close();
}
```

- Functionality includes:
	- opening and closing files
	- testing for successful open
	- reading input
	- looping over lines in a file

- `ifstream` used for working with input file
- `ifstream` evaluates to 0 when file opening fails
- full name `std::ifstream`

### `getline()`
```c++
int main(){
	ifstream jab("jabberwocky");
	if (!jab){
		cerr << "failed to open jabberwocky";
		exit(1);
	}
	
	string something;
	getline(jab,something);
	cout << something << endl; //"first line of file"
	jab.close();
}
```

### Token by Token

```c++
int main(){
	ifstream jab("jabberwocky");
	if (!jab){
		cerr << "failed to open jabberwocky";
		exit(1);
	}
	
	string something;
	while(jab >> something){
		cout << something << endl;
	}
	jab.close();
}
```

- read operation is located in a while condition
- loop stops when theres nothing left to read
- each read operation gets the next **whitespace delimited token** (the next non whitespace token)
	- `' '` - space
	- `\n` - new line
	- `\t` - tab

