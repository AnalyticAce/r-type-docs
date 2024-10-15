

# Struct EndpointHash



[**ClassList**](annotated.md) **>** [**EndpointHash**](structEndpointHash.md)



_Hash function for UDP endpoints._ [More...](#detailed-description)

* `#include <Server.hpp>`





































## Public Functions

| Type | Name |
| ---: | :--- |
|  std::size\_t | [**operator()**](#function-operator()) (const boost::asio::ip::udp::endpoint & endpoint) const<br>_Generates a hash for a UDP endpoint._  |




























# Detailed Description


This structure provides a custom hash function used for hashing UDP endpoints (which include IP address and port). It is primarily used in unordered containers like `std::unordered_map` to efficiently store and retrieve client connections. 


    
## Public Functions Documentation




### function operator() 

_Generates a hash for a UDP endpoint._ 
```C++
inline std::size_t EndpointHash::operator() (
    const boost::asio::ip::udp::endpoint & endpoint
) const
```





**Parameters:**


* `endpoint` The UDP endpoint (IP address and port). 



**Returns:**

A hashed value representing the endpoint.


This function concatenates the IP address and port of the UDP endpoint into a single string and then hashes that string to produce a unique identifier. 


        

<hr>

------------------------------
The documentation for this class was generated from the following file `include/Server/Server.hpp`

