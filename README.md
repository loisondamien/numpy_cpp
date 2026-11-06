  # numpy_cpp

  **A NumPy-compatible N-dimensional array library written in pure C++, with a Python interface.**

  `numpy_cpp` reimplements NumPy from scratch in modern C++ — **99.9% compatible with
  NumPy, exposing the exact same interface** — so code written against NumPy runs
  against `numpy_cpp` with little to no change, while gaining native C++ performance.

  ## Features

  - **NDArray** — multi-dimensional array class with full NumPy-like semantics
    (broadcasting, slicing, fancy indexing, views)
  - **Mathematical functions** — `sin`, `cos`, `exp`, `log`, `sqrt`, and more
  - **Linear algebra** — `dot`, `matmul`, `solve`, `inv`, `svd`, `qr`, `eig`
  - **Random number generation** — multiple distributions with modern generators
  - **FFT** — fast Fourier transform operations
  - **Statistics** — `mean`, `std`, `var`, `histogram`, `percentile`
  - **SIMD optimizations** — AVX2 / AVX-512 accelerated sorting and operations

  ## Requirements

  - A C++20 compiler (MSVC 2022/2026, GCC 11+, or Clang 14+)
  - *Optional:* Intel MKL — optimized linear algebra
  - *Optional:* Intel IPP — additional performance
  - *Optional:* Boost Math — special functions

  ## Usage — C++

  `numpy_cpp` is header-only; just include the headers:

  ```cpp
  #include <numpy/np_ndarray.h>
  #include <numpy/np_linalg.h>
  #include <numpy/np_random.h>
  // ...or include everything:
  #include <numpy/numpy.h>

  using namespace numpy;

  int main() {
      NDArray<double> a = np::arange<double>(12).reshape({3, 4});
      NDArray<double> b = np::ones<double>({4, 2});

      auto c = np::dot(a, b);              // matrix product
      auto mean_val = np::mean(a);         // statistics
      auto [u, s, vh] = np::linalg::svd(a); // linear algebra

      Generator gen(42);
      auto r = gen.random({3, 3});         // random numbers
  }

  Usage — Python

  The same API is exposed to Python, so existing NumPy code works unchanged:

  import numpycore as np   # drop-in: same interface as numpy

  a = np.arange(12).reshape((3, 4))
  b = np.ones((4, 2))
  c = np.dot(a, b)

  print(c.shape, np.mean(a), np.std(a))

  Documentation

  Full API documentation is generated with Sphinx — see the docs/ build output.

  License

  MIT (LICENSE)
