

# File Vector.hpp

[**File List**](files.md) **>** [**GameLogic**](dir_43a675281a639807a8e84134baca4472.md) **>** [**Vector.hpp**](GameLogic_2Vector_8hpp.md)

[Go to the documentation of this file](GameLogic_2Vector_8hpp.md)


```C++
/*
** EPITECH PROJECT, 2023
** B-OOP-400-COT-4-1-raytracer-shalom.dosseh
** File description:
** Vector.hpp
*/

#ifndef VECTOR_HPP_
#define VECTOR_HPP_
#include <algorithm>
#include <array>
#include <cctype>
#include <cmath>
#include <fstream>
#include <iostream>
#include <limits>
#include <map>
#include <memory>
#include <regex>
#include <sstream>
#include <stdexcept>
#include <string>
#include <tuple>
#include <vector>

class Vector2D {
public:
  double x; 
  double y; 

  Vector2D() : x(0), y(0) {}

  Vector2D(double x, double y) : x(x), y(y) {}

  double length() const { return std::sqrt(x * x + y * y); }

  Vector2D vector_unit() const { return *this / length(); }

  Vector2D &operator/=(double scalar) {
    x /= scalar;
    y /= scalar;
    return *this;
  }

  Vector2D operator/(double scalar) const {
    Vector2D result(*this);
    result /= scalar;
    return result;
  }

  double dot(const Vector2D &other) const { return x * other.x + y * other.y; }

  double length_squared() const { return x * x + y * y; }

  Vector2D normalize() {
    double length = std::sqrt(x * x + y * y);
    return Vector2D(x / length, y / length);
  }

  /*
   * @brief add two vectors
   * @param vector v
   * @return Vector2D&
   */
  Vector2D &add(const Vector2D &v) {
    x += v.x;
    y += v.y;
    return *this;
  }

  Vector2D &scale(double scalar) {
    x *= scalar;
    y *= scalar;
    return *this;
  }

  /*
   * @brief rotate the vector by an angle
   * @param double angle
   * @return Vector2D&
   */

  Vector2D &rotate(double angle) {
    double rad = angle * M_PI / 180;
    double c = cos(rad);
    double s = sin(rad);
    double nx = x * c - y * s;
    double ny = x * s + y * c;
    x = nx;
    y = ny;
    return *this;
  }
};

Vector2D operator+(const Vector2D &u, const Vector2D &v);

Vector2D operator-(const Vector2D &p, const Vector2D &n);

Vector2D operator*(double scalar, const Vector2D &v);

Vector2D operator*(const Vector2D &v, int scalar);

#endif /* !VECTOR_HPP_ */
```


