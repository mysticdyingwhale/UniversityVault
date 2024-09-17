# Multithreading
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