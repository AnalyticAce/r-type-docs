

# Struct parameter\_t



[**ClassList**](annotated.md) **>** [**parameter\_t**](structparameter__t.md)



_Structure representing a command-line parameter._ [More...](#detailed-description)

* `#include <Server.hpp>`





















## Public Attributes

| Type | Name |
| ---: | :--- |
|  std::function&lt; bool(int \*, char \*\*)&gt; | [**add\_new\_param**](#variable-add_new_param)  <br> |
|  std::string | [**argument**](#variable-argument)  <br> |
|  int | [**check\_me**](#variable-check_me)  <br>_Flag or variable for validation or tracking purposes._  |
|  std::string | [**name**](#variable-name)  <br>_The name of the parameter (e.g., "port")._  |
|  std::string | [**usage**](#variable-usage)  <br> |












































# Detailed Description


This structure holds the necessary information for parsing and processing command-line arguments when starting the server. 


    
## Public Attributes Documentation




### variable add\_new\_param 


```C++
std::function<bool(int *, char **)> parameter_t::add_new_param;
```



Function pointer to process the argument and store it. 


        

<hr>



### variable argument 


```C++
std::string parameter_t::argument;
```



The argument passed via the command-line (e.g., "-p" for port). 


        

<hr>



### variable check\_me 

```C++
int parameter_t::check_me;
```




<hr>



### variable name 

```C++
std::string parameter_t::name;
```




<hr>



### variable usage 


```C++
std::string parameter_t::usage;
```



Usage instructions for this parameter (e.g., "--port
&lt;value&gt;"). 


        

<hr>

------------------------------
The documentation for this class was generated from the following file `include/Server/Server.hpp`

