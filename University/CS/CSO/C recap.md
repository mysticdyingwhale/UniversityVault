# C recap

#cs 
## Pointers

A pointer is a variable that contains the memory address of a variable

A variable name directly references a value, whereas a pointer indirectly references a value

Referencing a value through a pointer is called indirection 


Pointer declaration is the same as in C++

To declare multiple pointers, use * before each var declaration `int *p1, *p2`

Initialize pointers to 0, NULL, or an address

For pointing to nothing, NULL is preferred over 0.

```C
int y = 5;
int *yPtr = &y;
```


Pointer variables must be same type, and assigning an absolute address to a pointer is prohibited.


`malloc` is used because it allows for exact specification of memory space allocation, and because it is flexible with reallocation.

```c
int main()
{
	char *str;
	str = (char*)malloc(16);
	strcpy(str, "csciuacso20(nyu)");
	printf("String=%s,Address=%u\n",str,str);
	str=(char*)realloc(str,25);
	
}
```


Use `strcpy` when assigning values to char pointers.

`malloc` returns a void pointer. Always typecast for `malloc` and `calloc`.

`calloc` vs `malloc` in default value.


```c
int main()
{
	int *m;
	m = malloc(5);
	//memory leak!
	m = NULL;

	//do this instead:
	int *a;
	a = (int*) malloc(5);
	free(a);
	m = NULL;
}
```


```C
int * g(void)
{
	//invalid, unintialized pointer
	int *px;
	*px = 10;
	return px;
}

int * h(void)
{
	//invalid, variable cleared when out of scope of h()
	int x = 10;
	return &x;
}

int * z(void)
{
	//valid, pointer properly initialised with allocated memory
	int  *px;
	px = (int *)malloc(sizeof(int));
	*px = 10;
	return px;
}
```

Arithmetic:
`p[i] = *(p+i)`


### Stack Implementation

With this implementation, a pointer `topPtr` always points to the pointer to the first node of the stack. 

```C

#include <stdio.h>
#include <stdlib.h>


struct stackNode
{
	int data;
	struct stackNode *nextPtr;
};

typedef struct stackNode StackNode; //synonym for struct stacknode
typedef struct StackNode *StackNodePtr; //synon ym for StackNode*


void push(StackNodePtr *topPtr, int data);
int pop(StackNodePtr *topPtr);
int isEmpty(StackNodePtr topPtr);


int main()
{
	StackNodePtr stackPtr = NULL;
	int value;
}

void push(StackNodePtr *topPtr, int data)
{
	StackNodePtr newPtr = malloc(sizeof(StackNode));
	if(newPtr !=NULL)
	{
		newPtr->data = data;
		newPtr->nextPtr = *topPtr;
		*topPtr = newPtr;
	}
	else
	{
		printf("%d not inserted. No memory available", data);
	}
}


int pop(StackNodePtr *topPtr)
{
	StackNodePtr tempPtr = *topPtr;
	int popValue = (*topPtr)->data;
	*topPtr = (*topPtr)->nextPtr;
	free(tempPtr);
	return popValue;
}

int isEmpty(StackNodePtr topPtr)
{
	return topPtr == NULL;
}

```




## Queue

```C

#include <stdio.h>
#include <stdlib.h>


struct queueNode
{
	int data;
	struct queueNode *nextPtr;
};

typedef struct queueNode QueueNode; //synonym for struct queuenode
typedef struct QueueNode *QueueNodePtr; //synon ym for QueueNode*


void queue(QueueNodePtr *headPtr, int data);
int dequeue(QueueNodePtr *headPtr);
int isEmpty(QueueNodePtr headPtr);


int main()
{
	QueueNodePtr headPtr = NULL;
	QueueNodePtr tailPtr = NULL;
	int value;
}

void queue(QueueNodePtr *headPtr, QueueNodePtr *tailPtr, int data)
{
	QueueNodePtr newPtr = malloc(sizeof(QueueNode));
	if(newPtr !=NULL)
	{
		newPtr->data = data;
		newPtr->nextPtr = NULL;
		if(isEmpty(*headPtr))
		{
			*headPtr = newPtr;
		}
		else
		{
			(*tailPtr)->nextPtr = newPtr;
		}
	}
	else
	{
		printf("%d not inserted. No memory available", data);
	}
}


int dequeue(QueueNodePtr *headPtr, QueueNodePtr *tailptr )
{
	int value  = (*headPtr)->data;
	QueueNodePtr tempPtr = *headPtr;
	*headPtr = (*headPtr)->nextPtr;
	if(*headPtr == NULL)
	{
		*tailPtr = NULL;
	}	
	free(tempPtr);
	return value;
	
}

int isEmpty(StackNodePtr topPtr)
{
	return headPtr == NULL;
}

```
