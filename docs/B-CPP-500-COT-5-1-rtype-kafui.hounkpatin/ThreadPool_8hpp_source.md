

# File ThreadPool.hpp

[**File List**](files.md) **>** [**include**](dir_d44c64559bbebec7f509842c48db8b23.md) **>** [**Server**](dir_17f455aea618a06e8886390757d4c564.md) **>** [**ThreadPool.hpp**](ThreadPool_8hpp.md)

[Go to the documentation of this file](ThreadPool_8hpp.md)


```C++
/*
** EPITECH PROJECT, 2024
** threadpool
** File description:
** ThreadPool
*/

#ifndef THREADPOOL_HPP_
#define THREADPOOL_HPP_
#include <boost/asio.hpp>
#include <iostream>
#include <thread>
#include <vector>

class ThreadPool
{
public:
    ThreadPool(boost::asio::io_context &io_context, std::size_t num_threads)
        : io_context(io_context)
    {
        add_threads(num_threads);
    }

    ~ThreadPool() { release(); }

    void add_threads(std::size_t num_threads)
    {
        for (std::size_t i = 0; i < num_threads; ++i)
        {
            thread_pool.emplace_back([this]() { io_context.run(); });
        }
    }

    void remove_threads(std::size_t num_threads)
    {
        for (std::size_t i = 0; i < num_threads && !thread_pool.empty(); ++i)
        {
            if (thread_pool.back().joinable())
            {
                thread_pool.back().join();
            }
            thread_pool.pop_back();
        }
    }

    void release()
    {
        io_context.stop();
        for (auto &thread : thread_pool)
        {
            if (thread.joinable())
            {
                thread.join();
            }
        }
        thread_pool.clear();
    }

protected:
private:
    std::vector<std::thread> thread_pool; 
    boost::asio::io_context
        &io_context; 
};

#endif /* !THREADPOOL_HPP_ */
```


