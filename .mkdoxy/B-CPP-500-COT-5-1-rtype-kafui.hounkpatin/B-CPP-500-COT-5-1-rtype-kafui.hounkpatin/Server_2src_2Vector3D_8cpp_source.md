

# File Vector3D.cpp

[**File List**](files.md) **>** [**Server**](dir_f6675a7e1cd1d6d7f6e5e9669ead62e8.md) **>** [**src**](dir_35da1b20ef5d00fba1377c2ea4ffeb70.md) **>** [**Vector3D.cpp**](Server_2src_2Vector3D_8cpp.md)

[Go to the documentation of this file](Server_2src_2Vector3D_8cpp.md)


```C++
/*
** EPITECH PROJECT, 2023
** B-OOP-400-COT-4-1-raytracer-shalom.dosseh
** File description:
** Vector3D.cpp
*/

#include "../include/Vector.hpp"

Vector2D operator+(const Vector2D &u, const Vector2D &v) {
  return Vector2D(u.x + v.x, u.y + v.y);
}
Vector2D operator-(const Vector2D &p, const Vector2D &n) {
  return Vector2D(p.x - n.x, p.y - n.y);
}
Vector2D operator*(double scalar, const Vector2D &v) {
  return Vector2D(scalar * v.x, scalar * v.y);
}
Vector2D operator*(const Vector2D &v, int scalar) {
  return Vector2D(scalar * v.x, scalar * v.y);
}
Vector2D operator*=(Vector2D &v, double scalar) {
  v.x *= scalar;
  v.y *= scalar;
  return v;
}
```


