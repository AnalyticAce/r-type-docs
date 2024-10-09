

# Class ThreadPool



[**ClassList**](annotated.md) **>** [**ThreadPool**](classThreadPool.md)





* `#include <ThreadPool.hpp>`





































## Public Functions

| Type | Name |
| ---: | :--- |
|   | [**ThreadPool**](#function-threadpool) (boost::asio::io\_context & io\_context, std::size\_t num\_threads) <br> |
|  void | [**add\_threads**](#function-add_threads) (std::size\_t num\_threads) <br> |
|  void | [**release**](#function-release) () <br> |
|  void | [**remove\_threads**](#function-remove_threads) (std::size\_t num\_threads) <br> |
|   | [**~ThreadPool**](#function-threadpool) () <br> |




























## Public Functions Documentation




### function ThreadPool 

```C++
inline ThreadPool::ThreadPool (
    boost::asio::io_context & io_context,
    std::size_t num_threads
) 
```




<hr>



### function add\_threads 

```C++
inline void ThreadPool::add_threads (
    std::size_t num_threads
) 
```




<hr>



### function release 

```C++
inline void ThreadPool::release () 
```




<hr>



### function remove\_threads 

```C++
inline void ThreadPool::remove_threads (
    std::size_t num_threads
) 
```




<hr>



### function ~ThreadPool 

```C++
inline ThreadPool::~ThreadPool () 
```




<hr>

------------------------------
The documentation for this class was generated from the following file `src/Server/include/ThreadPool.hpp`

