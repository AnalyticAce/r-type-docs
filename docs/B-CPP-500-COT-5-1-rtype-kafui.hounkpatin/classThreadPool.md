

# Class ThreadPool



[**ClassList**](annotated.md) **>** [**ThreadPool**](classThreadPool.md)



_A class representing a thread pool for managing asynchronous tasks._ 

* `#include <ThreadPool.hpp>`





































## Public Functions

| Type | Name |
| ---: | :--- |
|   | [**ThreadPool**](#function-threadpool) (boost::asio::io\_context & io\_context, std::size\_t num\_threads) <br>_Constructs a_ [_**ThreadPool**_](classThreadPool.md) _with a specified number of threads._ |
|  void | [**add\_threads**](#function-add_threads) (std::size\_t num\_threads) <br>_Adds a specified number of threads to the pool._  |
|  void | [**release**](#function-release) () <br>_Releases all threads in the pool and stops the IO context._  |
|  void | [**remove\_threads**](#function-remove_threads) (std::size\_t num\_threads) <br>_Removes a specified number of threads from the pool._  |
|   | [**~ThreadPool**](#function-threadpool) () <br>_Destructor for_ [_**ThreadPool**_](classThreadPool.md) _. Cleans up and releases threads._ |




























## Public Functions Documentation




### function ThreadPool 

_Constructs a_ [_**ThreadPool**_](classThreadPool.md) _with a specified number of threads._
```C++
inline ThreadPool::ThreadPool (
    boost::asio::io_context & io_context,
    std::size_t num_threads
) 
```





**Parameters:**


* `io_context` The IO context for managing asynchronous operations. 
* `num_threads` The number of threads to create in the pool. 




        

<hr>



### function add\_threads 

_Adds a specified number of threads to the pool._ 
```C++
inline void ThreadPool::add_threads (
    std::size_t num_threads
) 
```





**Parameters:**


* `num_threads` The number of threads to add. 




        

<hr>



### function release 

```C++
inline void ThreadPool::release () 
```




<hr>



### function remove\_threads 

_Removes a specified number of threads from the pool._ 
```C++
inline void ThreadPool::remove_threads (
    std::size_t num_threads
) 
```





**Parameters:**


* `num_threads` The number of threads to remove. 




        

<hr>



### function ~ThreadPool 

```C++
inline ThreadPool::~ThreadPool () 
```




<hr>

------------------------------
The documentation for this class was generated from the following file `include/Server/ThreadPool.hpp`

