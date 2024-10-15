

# Struct EndpointEqual



[**ClassList**](annotated.md) **>** [**EndpointEqual**](structEndpointEqual.md)



_Comparator for UDP endpoints._ [More...](#detailed-description)

* `#include <Server.hpp>`





































## Public Functions

| Type | Name |
| ---: | :--- |
|  bool | [**operator()**](#function-operator()) (const boost::asio::ip::udp::endpoint & lhs, const boost::asio::ip::udp::endpoint & rhs) const<br>_Compares two UDP endpoints._  |




























# Detailed Description


This structure provides a custom comparison function to compare two UDP endpoints. It is used to check if two endpoints (IP address and port) are equal. 


    
## Public Functions Documentation




### function operator() 

_Compares two UDP endpoints._ 
```C++
inline bool EndpointEqual::operator() (
    const boost::asio::ip::udp::endpoint & lhs,
    const boost::asio::ip::udp::endpoint & rhs
) const
```





**Parameters:**


* `lhs` The first UDP endpoint. 
* `rhs` The second UDP endpoint. 



**Returns:**

true If both endpoints have the same IP address and port. 




**Returns:**

false If the IP address or port of the endpoints differs. 





        

<hr>

------------------------------
The documentation for this class was generated from the following file `include/Server/Server.hpp`

