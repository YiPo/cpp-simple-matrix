
# cpp-simple-matrix

This is a fixed-size, 2D array template without numeric operations and boundary checking. Being useful to pass 2D data to a function, it is simple and handy to use rather than complicated building and configuration. However, if it's not what you are looking for. For a fully functional matrix on linear algebra, see [Eigen](http://eigen.tuxfamily.org/) or [Boost.uBLAS](https://www.google.com/search?q=boost+ublas). For a higher dimension array, see [Boost.MultiArray](https://www.google.com/search?q=boost+multiarray).

## Usage

Download the [`matrix.h`](https://raw.github.com/YiPo/cpp-simple-matrix/master/matrix.h) file and include it. No library has to be linked.

###### Example

```c++
#include "matrix.h"
#include <iostream>
using namespace std;

int main() {
	matrix<int> foo(1,3);
	
	foo.at(0,0)=1;
	foo(0,1)=8;
	foo[0][2]=3;
	
	cout<<"size: ";
	cout<<foo.get_m()<<"x";
	cout<<foo.get_n()<<endl;
	
	return 0;
}
```

## Reference

The `matrix` class template is defined as follows.

`template <typename T> class matrix;`

* `T`: the type of the elements

### Constructors

- `matrix()`                  (the default constructor)

- `matrix(int m, int n)`      constructs an m-by-n matrix.

- `matrix(const matrix &mat)` (the copy constructor)

### Member Functions

- `matrix &operator =` (the copy assignment)

- `int get_m() const`  returns the number of rows.

- `int get_n() const`  returns the number of columns.

###### element access

There are 3 ways to access the (i,j)th element.

| #  | declaration                   | description                        | example        |
|:---|:------------------------------|:-----------------------------------|:---------------|
| 1. | `T &at(int i, int j)`         | by the member function             | `foo.at(i, j)` |
| 2. | `T &operator ()`              | by a more compact syntax           | `foo(i, j)`    |
| 3. | `T &operator [] .operator []` | as a traditional 2D array (slower) | `foo[i][j]`    |

### Non-member functions

- `void swap(matrix<T> &a, matrix<T> &b)` exchanges the contents of two matrices.

