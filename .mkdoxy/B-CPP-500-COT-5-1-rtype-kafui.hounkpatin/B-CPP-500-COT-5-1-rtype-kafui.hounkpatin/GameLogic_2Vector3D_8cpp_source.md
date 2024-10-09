

# File Vector3D.cpp

[**File List**](files.md) **>** [**GameLogic**](dir_43a675281a639807a8e84134baca4472.md) **>** [**Vector3D.cpp**](GameLogic_2Vector3D_8cpp.md)

[Go to the documentation of this file](GameLogic_2Vector3D_8cpp.md)


```C++
/*
** EPITECH PROJECT, 2023
** B-OOP-400-COT-4-1-raytracer-shalom.dosseh
** File description:
** Vector3D.cpp
*/

#include "Vector.hpp"

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


