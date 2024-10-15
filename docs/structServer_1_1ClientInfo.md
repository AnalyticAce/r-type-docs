

# Struct Server::ClientInfo



[**ClassList**](annotated.md) **>** [**ClientInfo**](structServer_1_1ClientInfo.md)



_Structure containing information about connected clients._ [More...](#detailed-description)






















## Public Attributes

| Type | Name |
| ---: | :--- |
|  std::chrono::steady\_clock::time\_point | [**last\_ping**](#variable-last_ping)  <br>_Timestamp of the client's last ping._  |












































# Detailed Description


This structure tracks the last ping time of connected clients for managing connection status and timeouts. 


    
## Public Attributes Documentation




### variable last\_ping 

```C++
std::chrono::steady_clock::time_point Server::ClientInfo::last_ping;
```




<hr>

------------------------------
The documentation for this class was generated from the following file `include/Server/Server.hpp`

