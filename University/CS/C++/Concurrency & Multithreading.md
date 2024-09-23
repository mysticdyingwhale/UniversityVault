# Concurrency & Multithreading
#cs 

Multithreading in C++ works similarly to it does in C ([[Concurrency]]). 

Here is the syntax and keywords:

### `std::thread` 

```cpp
#include <iostream>
#include <thread>

void threadFunction() {
    std::cout << "Thread is running\n";
}

int main() {
    std::thread t(threadFunction); // Create a new thread that runs threadFunction
    t.join(); // Wait for the thread to finish
    return 0;
}
```


### `std::mutex` and `std::lock_guard`

```cpp
#include <iostream>
#include <thread>
#include <mutex>

std::mutex mtx;

void printThreadID(int id) {
    std::lock_guard<std::mutex> lock(mtx); // Lock the mutex
    std::cout << "Thread ID: " << id << std::endl;
    // Mutex is automatically released when lock goes out of scope
}

int main() {
    std::thread t1(printThreadID, 1);
    std::thread t2(printThreadID, 2);
    
    t1.join();
    t2.join();
    return 0;
}
```


### `std::condition_variable`

```cpp
#include <iostream>
#include <thread>
#include <mutex>
#include <condition_variable>

std::mutex mtx;
std::condition_variable cv;
bool ready = false;

void printID(int id) {
    std::unique_lock<std::mutex> lock(mtx);
    cv.wait(lock, []{ return ready; }); // Wait until ready is true
    std::cout << "Thread ID: " << id << std::endl;
}

void setReady() {
    {
        std::lock_guard<std::mutex> lock(mtx);
        ready = true;
    }
    cv.notify_all(); // Notify all waiting threads
}

int main() {
    std::thread t1(printID, 1);
    std::thread t2(printID, 2);
    
    std::this_thread::sleep_for(std::chrono::seconds(1));
    setReady();
    
    t1.join();
    t2.join();
    return 0;
}
```


### `std::async` & `std::future`

`std::future` is a class [[Templates|template]] which provides a means to access the outcomes of asynchronous operations. 

It is used to receive the result of an asynchronous operation in C++, which is managed using `std::async, std::packaged_task, std::promise`, which return an `std::future` object.

We use this `std::future` object to verify, await, or obtain the outcome of the operation.

We can only receive the result of the computation once in the program as the state of future is reset after getting the result.

```cpp
std::future<_type_> name;
```


#### Member functions of `std::future`

| Function       | Description                                                                                |
| -------------- | ------------------------------------------------------------------------------------------ |
| `get()`        | Get value received                                                                         |
| `wait()`       | Tell compiler to `wait()` for process to be done                                           |
| `wait_for()`   | Tell compiler to `wait()` for the specified time duration for the process to be finished   |
| `wait_until()` | Tell compiler to `wait()` until the specified time duration                                |
| `valid()`      | Checks if the `future()` object has a shared state, checks if its valid to perform `get()` |

Below is an example:

```cpp
// C++ Program to illustrate the use of std::future 
#include <chrono> 
#include <future> 
#include <iostream> 


// A simple function that returns some integer value 
int returnTwo() { return 2; } 

// driver code 
int main() 
{ 
	// creating a future object and a thread that executes 
	// the function returnTwo asynchronously 
	std::future<int> f = std::async(std::launch::async, returnTwo); 

	// getting and printing the result 
	std::cout << f.get(); 

	// trying for second time 
	std::cout << f.get(); 

	return 0; 
}
```


### `std::async`

`std::async` is a function template in C++ which allows for a function to be run asynchronously. 

This means that it executes the function in a separate thread or in the same thread as the caller, depending on launch policy.

This is useful for parallelizing tasks or performing background work without blocking the main thread.

Async has a few parameters. `policy` defines the behavior of the function:

`std::launch::async` - The function runs on a new thread

`std::launch::deferred` - The function is deferred, meaning it will run in the caller's thread when its result is needed (lazy evaluation.)

`std::launch::async | std::launch::deferred` - The system will choose whether to run asynchronously or to defer it.

```cpp
template <class Function, class... Args>
std::future<std::invoke_result_t<Function, Args...>> async(std::launch policy, Function&& f, Args&&... args);
```

