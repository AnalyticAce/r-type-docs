

# Class Score



[**ClassList**](annotated.md) **>** [**Score**](classScore.md)



_Component to manage an entity's score during gameplay._ [More...](#detailed-description)

* `#include <Entity.hpp>`





































## Public Functions

| Type | Name |
| ---: | :--- |
|   | [**Score**](#function-score) () <br>_Default constructor initializes the score to 0._  |
|  int | [**getScore**](#function-getscore) () const<br>_Retrieves the current score value._  |
|  void | [**set\_score**](#function-set_score) (int new\_score) <br>_Adds points to the current score._  |




























# Detailed Description


The score component is used to track points earned by entities. It supports incrementing the score and retrieving the current value. 


    
## Public Functions Documentation




### function Score 

```C++
inline Score::Score () 
```




<hr>



### function getScore 

_Retrieves the current score value._ 
```C++
inline int Score::getScore () const
```





**Returns:**

The current score of the entity. 





        

<hr>



### function set\_score 

_Adds points to the current score._ 
```C++
inline void Score::set_score (
    int new_score
) 
```





**Parameters:**


* `new_score` The number of points to add. 




        

<hr>

------------------------------
The documentation for this class was generated from the following file `include/Server/Entity.hpp`

