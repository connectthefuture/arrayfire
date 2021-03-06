Release Notes {#releasenotes}
==============

v3.4.0
==============

Major Updates
-------------
* [Sparse Matrix and BLAS](\ref sparse_func). <sup>[1](https://github.com/arrayfire/arrayfire/issues/821)
  [2](https://github.com/arrayfire/arrayfire/pull/1319)</sup>
* Faster JIT for CUDA and OpenCL. <sup>[1](https://github.com/arrayfire/arrayfire/issues/1472)
  [2](https://github.com/arrayfire/arrayfire/pull/1462)</sup>
* Support for [random number generator engines](\ref af::randomEngine).
  <sup>[1](https://github.com/arrayfire/arrayfire/issues/868)
  [2](https://github.com/arrayfire/arrayfire/pull/1551)</sup>
* Improvements to graphics. <sup>[1](https://github.com/arrayfire/arrayfire/pull/1555)
  [2](https://github.com/arrayfire/arrayfire/pull/1566)</sup>

Features
----------
* **[Sparse Matrix and BLAS](\ref sparse_func)** <sup>[1](https://github.com/arrayfire/arrayfire/issues/821)
[2](https://github.com/arrayfire/arrayfire/pull/1319)</sup>
  * Support for [CSR](\ref AF_STORAGE_CSR) and [COO](\ref AF_STORAGE_COO)
    [storage types](\ref af_storage).
  * Sparse-Dense Matrix Multiplication and Matrix-Vector Multiplication as a
    part of af::matmul() using \ref AF_STORAGE_CSR format for sparse.
  * Conversion to and from [dense](\ref AF_STORAGE_DENSE) matrix to [CSR](\ref AF_STORAGE_CSR)
    and [COO](\ref AF_STORAGE_COO) [storage types](\ref af_storage).
* **Faster JIT** <sup>[1](https://github.com/arrayfire/arrayfire/issues/1472)
  [2](https://github.com/arrayfire/arrayfire/pull/1462)</sup>
  * Performance improvements for CUDA and OpenCL JIT functions.
  * Support for evaluating multiple outputs in a single kernel. See af::array::eval() for more.
* **[Random Number Generation](\ref af::randomEngine)**
  <sup>[1](https://github.com/arrayfire/arrayfire/issues/868)
  [2](https://github.com/arrayfire/arrayfire/pull/1551)</sup>
  * af::randomEngine(): A random engine class to handle setting the [type](af_random_type) and seed
    for random number generator engines.
  * Supported engine types are (\ref af_random_engine_type):
    * [Philox](http://www.thesalmons.org/john/random123/)
    * [Threefry](http://www.thesalmons.org/john/random123/)
    * [Mersenne Twister](http://www.math.sci.hiroshima-u.ac.jp/~m-mat/MT/MTGP/)
* **Graphics** <sup>[1](https://github.com/arrayfire/arrayfire/pull/1555)
  [2](https://github.com/arrayfire/arrayfire/pull/1566)</sup>
  * Using [Forge v0.9.0](https://github.com/arrayfire/forge/releases/tag/v0.9.0)
  * [Vector Field](\ref af::Window::vectorField) plotting functionality.
    <sup>[1](https://github.com/arrayfire/arrayfire/pull/1566)</sup>
  * Removed [GLEW](http://glew.sourceforge.net/) and replaced with [glbinding](https://github.com/cginternals/glbinding).
    * Removed usage of GLEW after support for MX (multithreaded) was dropped in v2.0.
      <sup>[1](https://github.com/arrayfire/arrayfire/issues/1540)</sup>
  * Multiple overlays on the same window are now possible.
    * Overlays support for same type of object (2D/3D)
    * Supported by af::Window::plot, af::Window::hist, af::Window::surface,
      af::Window::vectorField.
  * New API to set axes limits for graphs.
    * Draw calls do not automatically compute the limits. This is now under user control.
    * af::Window::setAxesLimits can be used to set axes limits automatically or manually.
    * af::Window::setAxesTitles can be used to set axes titles.
  * New API for plot and scatter:
    * af::Window::plot() and af::Window::scatter() now can handle 2D and 3D and determine appropriate order.
    * af_draw_plot_nd()
    * af_draw_plot_2d()
    * af_draw_plot_3d()
    * af_draw_scatter_nd()
    * af_draw_scatter_2d()
    * af_draw_scatter_3d()
* **New [interpolation methods](\ref af_interp_type)**
<sup>[1](https://github.com/arrayfire/arrayfire/issues/1562)</sup>
  * Applies to
    * \ref af::resize()
    * \ref af::transform()
    * \ref af::approx1()
    * \ref af::approx2()
* **Support for [complex mathematical functions](\ref mathfunc_mat)**
  <sup>[1](https://github.com/arrayfire/arrayfire/issues/1507)</sup>
  * Add complex support for \ref trig_mat, \ref af::sqrt(), \ref af::log().
* **af::medfilt1(): Median filter for 1-d signals** <sup>[1](https://github.com/arrayfire/arrayfire/pull/1479)</sup>
* <b>Generalized scan functions: \ref scan_func_scan and \ref scan_func_scanbykey</b>
  * Now supports inclusive or exclusive scans
  * Supports binary operations defined by \ref af_binary_op.
  <sup>[1](https://github.com/arrayfire/arrayfire/issues/388)</sup>
* **[Image Moments](\ref moments_mat) functions**
  <sup>[1](https://github.com/arrayfire/arrayfire/pull/1453)</sup>
* <b>Add af::getSizeOf() function for \ref af_dtype</b>
  <sup>[1](https://github.com/arrayfire/arrayfire/pull/1404)</sup>
* <b>Explicitly extantiate \ref af::array::device() for `void *</b>
  <sup>[1](https://github.com/arrayfire/arrayfire/issues/1503)</sup>

Bug Fixes
--------------
* Fixes to edge-cases in \ref morph_mat. <sup>[1](https://github.com/arrayfire/arrayfire/issues/1564)</sup>
* Makes JIT tree size consistent between devices. <sup>[1](https://github.com/arrayfire/arrayfire/issues/1457)</sup>
* Delegate higher-dimension in \ref convolve_mat to correct dimensions. <sup>[1](https://github.com/arrayfire/arrayfire/pull/1445)</sup>
* Indexing fixes with C++11. <sup>[1](https://github.com/arrayfire/arrayfire/pull/1426) [2](https://github.com/arrayfire/arrayfire/pull/1426)</sup>
* Handle empty arrays as inputs in various functions. <sup>[1](https://github.com/arrayfire/arrayfire/issues/799)</sup>
* Fix bug when single element input to af::median. <sup>[1](https://github.com/arrayfire/arrayfire/pull/1423)</sup>
* Fix bug in calculation of time from af::timeit(). <sup>[1](https://github.com/arrayfire/arrayfire/pull/1414)</sup>
* Fix bug in floating point numbers in af::seq. <sup>[1](https://github.com/arrayfire/arrayfire/pull/1404)</sup>
* Fixes for OpenCL graphics interop on NVIDIA devices.
  <sup>[1](https://github.com/arrayfire/arrayfire/pull/1408/commits/e1f16e6)</sup>
* Fix bug when compiling large kernels for AMD devices.
  <sup>[1](https://github.com/arrayfire/arrayfire/pull/1465)</sup>
* Fix bug in af::bilateral when shared memory is over the limit.
  <sup>[1](https://github.com/arrayfire/arrayfire/pull/1478)</sup>
* Fix bug in kernel header compilation tool `bin2cpp`.
  <sup>[1](https://github.com/arrayfire/arrayfire/pull/1544)</sup>
* Fix inital values for \ref morph_mat functions.
  <sup>[1](https://github.com/arrayfire/arrayfire/pull/1547)</sup>
* Fix bugs in af::homography() CPU and OpenCL kernels.
  <sup>[1](https://github.com/arrayfire/arrayfire/pull/1584)</sup>
* Fix bug in CPU TNJ.
  <sup>[1](https://github.com/arrayfire/arrayfire/pull/1587)</sup>


Improvements
------------
* CUDA 8 and compute 6.x(Pascal) support, current installer ships with CUDA 7.5. <sup>[1](https://github.com/arrayfire/arrayfire/pull/1432) [2](https://github.com/arrayfire/arrayfire/pull/1487) [3](https://github.com/arrayfire/arrayfire/pull/1539)</sup>
* User controlled FFT plan caching. <sup>[1](https://github.com/arrayfire/arrayfire/pull/1448)</sup>
* CUDA performance improvements for \ref image_func_wrap, \ref image_func_unwrap and \ref approx_mat.
  <sup>[1](https://github.com/arrayfire/arrayfire/pull/1411)</sup>
* Fallback for CUDA-OpenGL interop when no devices does not support OpenGL.
  <sup>[1](https://github.com/arrayfire/arrayfire/pull/1415)</sup>
* Additional forms of batching with the \ref transform_func_transform functions.
  [New behavior defined here](https://github.com/arrayfire/arrayfire/pull/1412).
  <sup>[1](https://github.com/arrayfire/arrayfire/pull/1412)</sup>
* Update to OpenCL2 headers. <sup>[1](https://github.com/arrayfire/arrayfire/issues/1344)</sup>
* Support for integration with external OpenCL contexts. <sup>[1](https://github.com/arrayfire/arrayfire/pull/1140)</sup>
* Performance improvements to interal copy in CPU Backend.
  <sup>[1](https://github.com/arrayfire/arrayfire/pull/1440)</sup>
* Performance improvements to af::select and af::replace CUDA kernels.
  <sup>[1](https://github.com/arrayfire/arrayfire/pull/1587)</sup>
* Enable OpenCL-CPU offload by default for devices with Unified Host Memory.
  <sup>[1](https://github.com/arrayfire/arrayfire/pull/1521)</sup>
  * To disable, use the environment variable `AF_OPENCL_CPU_OFFLOAD=0`.

Build
------
* Compilation speedups. <sup>[1](https://github.com/arrayfire/arrayfire/pull/1526)</sup>
* Build fixes with MKL. <sup>[1](https://github.com/arrayfire/arrayfire/pull/1526)</sup>
* Error message when CMake CUDA Compute Detection fails. <sup>[1](https://github.com/arrayfire/arrayfire/issues/1535)</sup>
* Several CMake build issues with Xcode generator fixed.
  <sup>[1](https://github.com/arrayfire/arrayfire/pull/1493) [2](https://github.com/arrayfire/arrayfire/pull/1499)</sup>
* Fix multiple OpenCL definitions at link time. <sup>[1](https://github.com/arrayfire/arrayfire/issues/1429)</sup>
* Fix lapacke detection in CMake. <sup>[1](https://github.com/arrayfire/arrayfire/pull/1423)</sup>
* Update build tags of
  * [clBLAS](https://github.com/clMathLibraries/clBLAS)
  * [clFFT](https://github.com/clMathLibraries/clFFT)
  * [Boost.Compute](https://github.com/boostorg/compute)
  * [Forge](https://github.com/arrayfire/forge)
  * [glbinding](https://github.com/cginternals/glbinding)
* Fix builds with GCC 6.1.1 and GCC 5.3.0. <sup>[1](https://github.com/arrayfire/arrayfire/pull/1409)</sup>

Installers
----------
* All installers now ship with ArrayFire libraries build with MKL 2016.
* All installers now ship with Forge development files and examples included.
* CUDA Compute 2.0 has been removed from the installers. Please contact us
  directly if you have a special need.

Examples
-------------
* Added [example simulating gravity](\ref graphics/field.cpp) for
  demonstration of vector field.
* Improvements to \ref financial/black_scholes_options.cpp example.
* Improvements to \ref graphics/gravity_sim.cpp example.
* Fix graphics examples to use af::Window::setAxesLimits and
  af::Window::setAxesTitles functions.

Documentation & Licensing
-------------------------
* [ArrayFire copyright and trademark policy](http://arrayfire.com/trademark-policy)
* Fixed grammar in license.
* Add license information for glbinding.
* Remove license infomation for GLEW.
* Random123 now applies to all backends.
* Random number functions are now under \ref random_mat.

Deprecations
------------
The following functions have been deprecated and may be modified or removed
permanently from future versions of ArrayFire.
* \ref af::Window::plot3(): Use \ref af::Window::plot instead.
* \ref af_draw_plot(): Use \ref af_draw_plot_nd or \ref af_draw_plot_2d instead.
* \ref af_draw_plot3(): Use \ref af_draw_plot_nd or \ref af_draw_plot_3d instead.
* \ref af::Window::scatter3(): Use \ref af::Window::scatter instead.
* \ref af_draw_scatter(): Use \ref af_draw_scatter_nd or \ref af_draw_scatter_2d instead.
* \ref af_draw_scatter3(): Use \ref af_draw_scatter_nd or \ref af_draw_scatter_3d instead.

Known Issues
-------------
Certain CUDA functions are known to be broken on Tegra K1. The following ArrayFire tests are currently failing:
* assign_cuda
* harris_cuda
* homography_cuda
* median_cuda
* orb_cudasort_cuda
* sort_by_key_cuda
* sort_index_cuda


v3.3.2
==============

Improvements
------------
* Family of [Sort](\ref sort_mat) functions now support
  [higher order dimensions](https://github.com/arrayfire/arrayfire/pull/1373).
* Improved performance of batched sort on dim 0 for all [Sort](\ref sort_mat) functions.
* [Median](\ref stat_func_median) now also supports higher order dimensions.

Bug Fixes
--------------

* Fixes to [error handling](https://github.com/arrayfire/arrayfire/issues/1352) in C++ API for binary functions.
* Fixes to [external OpenCL context management](https://github.com/arrayfire/arrayfire/issues/1350).
* Fixes to [JPEG_GREYSCALE](https://github.com/arrayfire/arrayfire/issues/1360) for FreeImage versions <= 3.154.
* Fixed for [non-float inputs](https://github.com/arrayfire/arrayfire/issues/1386) to \ref af::rgb2gray().

Build
------
* [Disable CPU Async](https://github.com/arrayfire/arrayfire/issues/1378) when building with GCC < 4.8.4.
* Add option to [disable CPUID](https://github.com/arrayfire/arrayfire/issues/1369) from CMake.
* More verbose message when [CUDA Compute Detection fails](https://github.com/arrayfire/arrayfire/issues/1362).
* Print message to use [CUDA library stub](https://github.com/arrayfire/arrayfire/issues/1363)
  from CUDA Toolkit if CUDA Library is not found from default paths.
* [Build Fixes](https://github.com/arrayfire/arrayfire/pull/1385) on Windows.
  * For compiling tests our of source.
  * For compiling ArrayFire with static MKL.
* [Exclude <sys/sysctl.h>](https://github.com/arrayfire/arrayfire/pull/1368) when building on GNU Hurd.
* Add [manual CMake options](https://github.com/arrayfire/arrayfire/pull/1389) to build DEB and RPM packages.

Documentation
-------------
* Fixed documentation for \ref af::replace().
* Fixed images in [Using on OSX](\ref using_on_osx) page.

Installer
---------
* Linux x64 installers will now be compiled with GCC 4.9.2.
* OSX installer gives better error messages on brew failures and
  now includes link to [Fixing OS X Installer Failures] (https://github.com/arrayfire/arrayfire/wiki/Fixing-Common-OS-X-Installer-Failures)
  for brew installation failures.

v3.3.1
==============

Bug Fixes
--------------

* Fixes to \ref af::array::device()
    * CPU Backend: [evaluate arrays](https://github.com/arrayfire/arrayfire/issues/1316)
      before returning pointer with asynchronous calls in CPU backend.
    * OpenCL Backend: [fix segfaults](https://github.com/arrayfire/arrayfire/issues/1324)
      when requested for device pointers on empty arrays.
* Fixed \ref af::array::operator%() from using [rem to mod](https://github.com/arrayfire/arrayfire/issues/1318).
* Fixed [array destruction](https://github.com/arrayfire/arrayfire/issues/1321)
  when backends are switched in Unified API.
* Fixed [indexing](https://github.com/arrayfire/arrayfire/issues/1331) after
  \ref af::moddims() is called.
* Fixes FFT calls for CUDA and OpenCL backends when used on
  [multiple devices](https://github.com/arrayfire/arrayfire/issues/1332).
* Fixed [unresolved external](https://github.com/arrayfire/arrayfire/commit/32965ef)
  for some functions from \ref af::array::array_proxy class.

Build
------
* CMake compiles files in alphabetical order.
* CMake fixes for BLAS and LAPACK on some Linux distributions.

Improvements
------------
* Fixed [OpenCL FFT performance](https://github.com/arrayfire/arrayfire/issues/1323) regression.
* \ref af::array::device() on OpenCL backend [returns](https://github.com/arrayfire/arrayfire/issues/1311)
  `cl_mem` instead of `(void*)cl::Buffer*`.
* In Unified backend, [load versioned libraries](https://github.com/arrayfire/arrayfire/issues/1312)
  at runtime.

Documentation
------
* Reorganized, cleaner README file.
* Replaced non-free lena image in assets with free-to-distribute lena image.

v3.3.0
==============

Major Updates
-------------

* CPU backend supports aysnchronous execution.
* Performance improvements to OpenCL BLAS and FFT functions.
* Improved performance of memory manager.
* Improvements to visualization functions.
* Improved sorted order for OpenCL devices.
* Integration with external OpenCL projects.

Features
----------

* \ref af::getActiveBackend(): Returns the current backend being used.
* [Scatter plot](https://github.com/arrayfire/arrayfire/pull/1116) added to graphics.
* \ref af::transform() now supports perspective transformation matrices.
* \ref af::infoString(): Returns `af::info()` as a string.
* \ref af::printMemInfo(): Print a table showing information about buffer from the memory manager
    * The \ref AF_MEM_INFO macro prints numbers and total sizes of all buffers (requires including af/macros.h)
* \ref af::allocHost(): Allocates memory on host.
* \ref af::freeHost(): Frees host side memory allocated by arrayfire.
* OpenCL functions can now use CPU implementation.
    * Currently limited to Unified Memory devices (CPU and On-board Graphics).
    * Functions: af::matmul() and all [LAPACK](\ref linalg_mat) functions.
    * Takes advantage of optimized libraries such as MKL without doing memory copies.
    * Use the environment variable `AF_OPENCL_CPU_OFFLOAD=1` to take advantage of this feature.
* Functions specific to OpenCL backend.
    * \ref afcl::addDevice(): Adds an external device and context to ArrayFire's device manager.
    * \ref afcl::deleteDevice(): Removes an external device and context from ArrayFire's device manager.
    * \ref afcl::setDevice(): Sets an external device and context from ArrayFire's device manager.
    * \ref afcl::getDeviceType(): Gets the device type of the current device.
    * \ref afcl::getPlatform(): Gets the platform of the current device.
* \ref af::createStridedArray() allows [array creation user-defined strides](https://github.com/arrayfire/arrayfire/issues/1177) and device pointer.
* [Expose functions](https://github.com/arrayfire/arrayfire/issues/1131) that provide information
  about memory layout of Arrays.
    * \ref af::getStrides(): Gets the strides for each dimension of the array.
    * \ref af::getOffset(): Gets the offsets for each dimension of the array.
    * \ref af::getRawPtr(): Gets raw pointer to the location of the array on device.
    * \ref af::isLinear(): Returns true if all elements in the array are contiguous.
    * \ref af::isOwner(): Returns true if the array owns the raw pointer, false if it is a sub-array.
    * \ref af::getStrides(): Gets the strides of the array.
    * \ref af::getStrides(): Gets the strides of the array.
* \ref af::getDeviceId(): Gets the device id on which the array resides.
* \ref af::isImageIOAvailable(): Returns true if ArrayFire was compiled with Freeimage enabled
* \ref af::isLAPACKAvailable(): Returns true if ArrayFire was compiled with LAPACK functions enabled

Bug Fixes
--------------

* Fixed [errors when using 3D / 4D arrays](https://github.com/arrayfire/arrayfire/pull/1251) in select and replace
* Fixed [JIT errors on AMD devices](https://github.com/arrayfire/arrayfire/pull/1238) for OpenCL backend.
* Fixed [imageio bugs](https://github.com/arrayfire/arrayfire/pull/1229) for 16 bit images.
* Fixed [bugs when loading and storing images](https://github.com/arrayfire/arrayfire/pull/1228) natively.
* Fixed [bug in FFT for NVIDIA GPUs](https://github.com/arrayfire/arrayfire/issues/615) when using OpenCL backend.
* Fixed [bug when using external context](https://github.com/arrayfire/arrayfire/pull/1241) with OpenCL backend.
* Fixed [memory leak](https://github.com/arrayfire/arrayfire/issues/1269) in \ref af_median_all().
* Fixed [memory leaks and performance](https://github.com/arrayfire/arrayfire/pull/1274) in graphics functions.
* Fixed [bugs when indexing followed by moddims](https://github.com/arrayfire/arrayfire/issues/1275).
* \ref af_get_revision() now returns actual commit rather than AF_REVISION.
* Fixed [releasing arrays](https://github.com/arrayfire/arrayfire/issues/1282) when using different backends.
* OS X OpenCL: [LAPACK functions](\ref linalg_mat) on CPU devices use OpenCL offload (previously threw errors).
* [Add support for 32-bit integer image types](https://github.com/arrayfire/arrayfire/pull/1287) in Image IO.
* Fixed [set operations for row vectors](https://github.com/arrayfire/arrayfire/issues/1300)
* Fixed [bugs](https://github.com/arrayfire/arrayfire/issues/1243) in \ref af::meanShift() and af::orb().

Improvements
--------------

* Optionally [offload BLAS and LAPACK](https://github.com/arrayfire/arrayfire/pull/1221) functions to CPU implementations to improve performance.
* Performance improvements to the memory manager.
* Error messages are now more detailed.
* Improved sorted order for OpenCL devices.
* JIT heuristics can now be tweaked using environment variables. See
  [Environment Variables](\ref configuring_environment) tutorial.
* Add `BUILD_<BACKEND>` [options to examples and tests](https://github.com/arrayfire/arrayfire/issues/1286)
  to toggle backends when compiling independently.

Examples
----------

* New visualization [example simulating gravity](\ref graphics/gravity_sim.cpp).

Build
----------

* Support for Intel `icc` compiler
* Support to compile with Intel MKL as a BLAS and LAPACK provider
* Tests are now available for building as standalone (like examples)
* Tests can now be built as a single file for each backend
* Better handling of NONFREE build options
* [Searching for GLEW in CMake default paths](https://github.com/arrayfire/arrayfire/pull/1292)
* Fixes for compiling with MKL on OSX.

Installers
----------
* Improvements to OSX Installer
    * CMake config files are now installed with libraries
    * Independent options for installing examples and documentation components

Deprecations
-----------

* `af_lock_device_arr` is now deprecated to be removed in v4.0.0. Use \ref af_lock_array() instead.
* `af_unlock_device_arr` is now deprecated to be removed in v4.0.0. use \ref af_unlock_array() instead.

Documentation
--------------

* Fixes to documentation for \ref matchTemplate().
* Improved documentation for deviceInfo.
* Fixes to documentation for \ref exp().

Known Issues
------------

* [Solve OpenCL fails on NVIDIA Maxwell devices](https://github.com/arrayfire/arrayfire/issues/1246)
  for f32 and c32 when M > N and K % 4 is 1 or 2.


v3.2.2
==============

Bug Fixes
--------------

* Fixed [memory leak](https://github.com/arrayfire/arrayfire/pull/1145) in
  CUDA Random number generators
* Fixed [bug](https://github.com/arrayfire/arrayfire/issues/1157) in
  af::select() and af::replace() tests
* Fixed [exception](https://github.com/arrayfire/arrayfire/issues/1164)
  thrown when printing empty arrays with af::print()
* Fixed [bug](https://github.com/arrayfire/arrayfire/issues/1170) in CPU
  random number generation. Changed the generator to
  [mt19937](http://en.cppreference.com/w/cpp/numeric/random)
* Fixed exception handling (internal)
    * [Exceptions](https://github.com/arrayfire/arrayfire/issues/1188)
      now show function, short file name and line number
    * Added [AF_RETURN_ERROR](https://github.com/arrayfire/arrayfire/issues/1186)
      macro to handle returning errors.
    * Removed THROW macro, and renamed AF_THROW_MSG to AF_THROW_ERR.
* Fixed [bug](https://github.com/arrayfire/arrayfire/commit/9459c6)
  in \ref af::identity() that may have affected CUDA Compute 5.2 cards


Build
------
* Added a [MIN_BUILD_TIME](https://github.com/arrayfire/arrayfire/issues/1193)
  option to build with minimum optimization compiler flags resulting in faster
  compile times
* Fixed [issue](https://github.com/arrayfire/arrayfire/issues/1143) in CBLAS
  detection by CMake
* Fixed tests failing for builds without optional components
  [FreeImage](https://github.com/arrayfire/arrayfire/issues/1143) and
  [LAPACK](https://github.com/arrayfire/arrayfire/issues/1167)
* Added a [test](https://github.com/arrayfire/arrayfire/issues/1192)
  for unified backend
* Only [info and backend tests](https://github.com/arrayfire/arrayfire/issues/1192)
  are now built for unified backend
* [Sort tests](https://github.com/arrayfire/arrayfire/issues/1199)
  execution alphabetically
* Fixed compilation flags and errors in tests and examples
* [Moved AF_REVISION and AF_COMPILER_STR](https://github.com/arrayfire/arrayfire/commit/2287c5)
  into src/backend. This is because as revision is updated with every commit,
  entire ArrayFire would have to be rebuilt in the old code.
    * v3.3 will add a af_get_revision() function to get the revision string.
* [Clean up examples](https://github.com/arrayfire/arrayfire/pull/1158)
    * Remove getchar for Windows (this will be handled by the installer)
    * Other miscellaneous code cleanup
    * Fixed bug in [plot3.cpp](\ref graphics/plot3.cpp) example
* [Rename](https://github.com/arrayfire/arrayfire/commit/35f0fc2) clBLAS/clFFT
  external project suffix from external -> ext
* [Add OpenBLAS](https://github.com/arrayfire/arrayfire/pull/1197) as a
  lapack/lapacke alternative

Improvements
------------
* Added \ref AF_MEM_INFO macro to print memory info from ArrayFire's memory
  manager ([cross issue](https://github.com/arrayfire/arrayfire/issues/1172))
* Added [additional paths](https://github.com/arrayfire/arrayfire/issues/1184)
  for searching for `libaf*` for Unified backend on unix-style OS.
    * Note: This still requires dependencies such as forge, CUDA, NVVM etc to be
      in `LD_LIBRARY_PATH` as described in [Unified Backend](\ref unifiedbackend)
* [Create streams](https://github.com/arrayfire/arrayfire/commit/ed0373f)
  for devices only when required in CUDA Backend

Documentation
------
* [Hide scrollbars](https://github.com/arrayfire/arrayfire/commit/9d218a5)
  appearing for pre and code styles
* Fix [documentation](https://github.com/arrayfire/arrayfire/commit/ac09f91) for af::replace
* Add [code sample](https://github.com/arrayfire/arrayfire/commit/4e06483)
  for converting the output of af::getAvailableBackends() into bools
* Minor fixes in documentation

v3.2.1
==============

Bug Fixes
--------------

* Fixed [bug](https://github.com/arrayfire/arrayfire/pull/1136) in homography()
* Fixed [bug](https://github.com/arrayfire/arrayfire/issues/1135) in behavior
  of af::array::device()
* Fixed [bug](https://github.com/arrayfire/arrayfire/issues/1129) when
  indexing with span along trailing dimension
* Fixed [bug](https://github.com/arrayfire/arrayfire/issues/1127) when
  indexing in [GFor](\ref gfor)
* Fixed [bug](https://github.com/arrayfire/arrayfire/issues/1122) in CPU
  information fetching
* Fixed compilation [bug](https://github.com/arrayfire/arrayfire/issues/1117)
  in unified backend caused by missing link library
* Add [missing symbol](https://github.com/arrayfire/arrayfire/pull/1114) for
  af_draw_surface()

Build
------
* Tests can now be used as a [standalone project](https://github.com/arrayfire/arrayfire/pull/1120)
    * Tests can now be built using pre-compiled libraries
    * Similar to how the examples are built
* The install target now installs the examples source irrespective of the
  BUILD_EXAMPLES value
    * Examples are not built if BUILD_EXAMPLES is off

Documentation
------
* HTML documentation is now [built and installed](https://github.com/arrayfire/arrayfire/pull/1109)
  in docs/html
* Added documentation for \ref af::seq class
* Updated [Matrix Manipulation](\ref matrixmanipulation) tutorial
* Examples list is now generated by CMake
    * <a href="examples.htm">Examples</a> are now listed as dir/example.cpp
* Removed dummy groups used for indexing documentation (affcted doxygen < 1.8.9)

v3.2.0
=================

Major Updates
-------------

* Added Unified backend
    * Allows switching backends at runtime
    * Read [Unified Backend](\ref unifiedbackend) for more.
* Support for 16-bit integers (\ref s16 and \ref u16)
    * All functions that support 32-bit interger types (\ref s32, \ref u32),
      now also support 16-bit interger types

Function Additions
------------------
* Unified Backend
    * \ref setBackend() - Sets a backend as active
    * \ref getBackendCount() - Gets the number of backends available for use
    * \ref getAvailableBackends() - Returns information about available backends
    * \ref getBackendId() - Gets the backend enum for an array

* Vision
    * \ref homography() - Homography estimation
    * \ref gloh() - GLOH Descriptor for SIFT

* Image Processing
    * \ref loadImageNative() - Load an image as native data without modification
    * \ref saveImageNative() - Save an image without modifying data or type

* Graphics
    * \ref af::Window::plot3() - 3-dimensional line plot
    * \ref af::Window::surface() - 3-dimensional curve plot

* Indexing
    * \ref af_create_indexers()
    * \ref af_set_array_indexer()
    * \ref af_set_seq_indexer()
    * \ref af_set_seq_param_indexer()
    * \ref af_release_indexers()

* CUDA Backend Specific
    * \ref setNativeId() - Set the CUDA device with given native id as active
        * ArrayFire uses a modified order for devices. The native id for a
          device can be retreived using `nvidia-smi`

* OpenCL Backend Specific
    * \ref setDeviceId() - Set the OpenCL device using the `clDeviceId`

Other Improvements
------------------------
* Added \ref c32 and \ref c64 support for \ref isNaN(), \ref isInf() and \ref iszero()
* Added CPU information for `x86` and `x86_64` architectures in CPU backend's \ref info()
* Batch support for \ref approx1() and \ref approx2()
    * Now can be used with gfor as well
* Added \ref s64 and \ref u64 support to:
    * \ref sort() (along with sort index and sort by key)
    * \ref setUnique(), \ref setUnion(), \ref setIntersect()
    * \ref convolve() and \ref fftConvolve()
    * \ref histogram() and \ref histEqual()
    * \ref lookup()
    * \ref mean()
* Added \ref AF_MSG macro

Build Improvements
------------------
* Submodules update is now automatically called if not cloned recursively
* [Fixes for compilation](https://github.com/arrayfire/arrayfire/issues/766) on Visual Studio 2015
* Option to use [fallback to CPU LAPACK](https://github.com/arrayfire/arrayfire/pull/1053)
  for linear algebra functions in case of CUDA 6.5 or older versions.

Bug Fixes
--------------
* Fixed [memory leak](https://github.com/arrayfire/arrayfire/pull/1096) in \ref susan()
* Fixed [failing test](https://github.com/arrayfire/arrayfire/commit/144a2db)
  in \ref lower() and \ref upper() for CUDA compute 53
* Fixed [bug](https://github.com/arrayfire/arrayfire/issues/1092) in CUDA for indexing out of bounds
* Fixed [dims check](https://github.com/arrayfire/arrayfire/commit/6975da8) in \ref iota()
* Fixed [out-of-bounds access](https://github.com/arrayfire/arrayfire/commit/7fc3856) in \ref sift()
* Fixed [memory allocation](https://github.com/arrayfire/arrayfire/commit/5e88e4a) in \ref fast() OpenCL
* Fixed [memory leak](https://github.com/arrayfire/arrayfire/pull/994) in image I/O functions
* \ref dog() now returns float-point type arrays

Documentation Updates
---------------------
* Improved tutorials documentation
    * More detailed Using on [Linux](\ref using_on_linux), [OSX](\ref using_on_osx),
      [Windows](\ref using_on_windows) pages.
* Added return type information for functions that return different type
  arrays

New Examples
------------
* Graphics
    * [Plot3](\ref graphics/plot3.cpp)
    * [Surface](\ref graphics/surface.cpp)
* [Shallow Water Equation](\ref pde/swe.cpp)
* [Basic](\ref unified/basic.cpp) as a Unified backend example

Installers
-----------
* All installers now include the Unified backend and corresponding CMake files
* Visual Studio projects include Unified in the Platform Configurations
* Added installer for Jetson TX1
* SIFT and GLOH do not ship with the installers as SIFT is protected by
  patents that do not allow commercial distribution without licensing.

v3.1.3
==============

Bug Fixes
---------

* Fixed [bugs](https://github.com/arrayfire/arrayfire/issues/1042) in various OpenCL kernels without offset additions
* Remove ARCH_32 and ARCH_64 flags
* Fix [missing symbols](https://github.com/arrayfire/arrayfire/issues/1040) when freeimage is not found
* Use CUDA driver version for Windows
* Improvements to SIFT
* Fixed [memory leak](https://github.com/arrayfire/arrayfire/issues/1045) in median
* Fixes for Windows compilation when not using MKL [#1047](https://github.com/arrayfire/arrayfire/issues/1047)
* Fixed for building without LAPACK

Other
-------

* Documentation: Fixed documentation for select and replace
* Documentation: Fixed documentation for af_isnan

v3.1.2
==============

Bug Fixes
---------

* Fixed [bug](https://github.com/arrayfire/arrayfire/commit/4698f12) in assign that was causing test to fail
* Fixed bug in convolve. Frequency condition now depends on kernel size only
* Fixed [bug](https://github.com/arrayfire/arrayfire/issues/1005) in indexed reductions for complex type in OpenCL backend
* Fixed [bug](https://github.com/arrayfire/arrayfire/issues/1006) in kernel name generation in ireduce for OpenCL backend
* Fixed non-linear to linear indices in ireduce
* Fixed [bug](https://github.com/arrayfire/arrayfire/issues/1011) in reductions for small arrays
* Fixed [bug](https://github.com/arrayfire/arrayfire/issues/1010) in histogram for indexed arrays
* Fixed [compiler error](https://github.com/arrayfire/arrayfire/issues/1015) CPUID for non-compliant devices
* Fixed [failing tests](https://github.com/arrayfire/arrayfire/issues/1008) on i386 platforms
* Add missing AFAPI

Other
-------

* Documentation: Added missing examples and other corrections
* Documentation: Fixed warnings in documentation building
* Installers: Send error messages to log file in OSX Installer

v3.1.1
==============

Installers
-----------

* CUDA backend now depends on CUDA 7.5 toolkit
* OpenCL backend now require OpenCL 1.2 or greater

Bug Fixes
--------------

* Fixed [bug](https://github.com/arrayfire/arrayfire/issues/981) in reductions after indexing
* Fixed [bug](https://github.com/arrayfire/arrayfire/issues/976) in indexing when using reverse indices

Build
------

* `cmake` now includes `PKG_CONFIG` in the search path for CBLAS and LAPACKE libraries
* [heston_model.cpp](\ref financial/heston_model.cpp) example now builds with the default ArrayFire cmake files after installation

Other
------

* Fixed bug in [image_editing.cpp](\ref image_processing/image_editing.cpp)

v3.1.0
==============

Function Additions
------------------
* Computer Vision Functions
    * \ref nearestNeighbour() - Nearest Neighbour with SAD, SSD and SHD distances
    * \ref harris() - Harris Corner Detector
    * \ref susan() - Susan Corner Detector
    * \ref sift() - Scale Invariant Feature Transform (SIFT)
        * Method and apparatus for identifying scale invariant features"
          "in an image and use of same for locating an object in an image,\" David"
          "G. Lowe, US Patent 6,711,293 (March 23, 2004). Provisional application"
          "filed March 8, 1999. Asignee: The University of British Columbia. For"
          "further details, contact David Lowe (lowe@cs.ubc.ca) or the"
          "University-Industry Liaison Office of the University of British"
          "Columbia.")
        * SIFT is available for compiling but does not ship with ArrayFire
          hosted installers/pre-built libraries
    * \ref dog() -  Difference of Gaussians

* Image Processing Functions
    * \ref ycbcr2rgb() and \ref rgb2ycbcr() - RGB <->YCbCr color space conversion
    * \ref wrap() and \ref unwrap() Wrap and Unwrap
    * \ref sat() - Summed Area Tables
    * \ref loadImageMem() and \ref saveImageMem() - Load and Save images to/from memory
        * \ref af_image_format - Added imageFormat (af_image_format) enum

* Array & Data Handling
    * \ref copy() - Copy
    * array::lock() and array::unlock() - Lock and Unlock
    * \ref select() and \ref replace() - Select and Replace
    * Get array reference count (af_get_data_ref_count)

* Signal Processing
    * \ref fftInPlace() - 1D in place FFT
    * \ref fft2InPlace() - 2D in place FFT
    * \ref fft3InPlace() - 3D in place FFT
    * \ref ifftInPlace() - 1D in place Inverse FFT
    * \ref ifft2InPlace() - 2D in place Inverse FFT
    * \ref ifft3InPlace() - 3D in place Inverse FFT
    * \ref fftR2C() - Real to complex FFT
    * \ref fftC2R() - Complex to Real FFT

* Linear Algebra
    * \ref svd() and \ref svdInPlace() - Singular Value Decomposition

* Other operations
    * \ref sigmoid() - Sigmoid
    * Sum (with option to replace NaN values)
    * Product (with option to replace NaN values)

* Graphics
    * Window::setSize() - Window resizing using Forge API

* Utility
    * Allow users to set print precision (print, af_print_array_gen)
    * \ref saveArray() and \ref readArray() - Stream arrays to binary files
    * \ref toString() - toString function returns the array and data as a string

* CUDA specific functionality
    * \ref getStream() - Returns default CUDA stream ArrayFire uses for the current device
    * \ref getNativeId() - Returns native id of the CUDA device

Improvements
------------
* dot
    * Allow complex inputs with conjugate option
* AF_INTERP_LOWER interpolation
    * For resize, rotate and transform based functions
* 64-bit integer support
    * For reductions, random, iota, range, diff1, diff2, accum, join, shift
      and tile
* convolve
    * Support for non-overlapping batched convolutions
* Complex Arrays
    * Fix binary ops on complex inputs of mixed types
    * Complex type support for exp
* tile
    * Performance improvements by using JIT when possible.
* Add AF_API_VERSION macro
    * Allows disabling of API to maintain consistency with previous versions
* Other Performance Improvements
    * Use reference counting to reduce unnecessary copies
* CPU Backend
    * Device properties for CPU
    * Improved performance when all buffers are indexed linearly
* CUDA Backend
    * Use streams in CUDA (no longer using default stream)
    * Using async cudaMem ops
    * Add 64-bit integer support for JIT functions
    * Performance improvements for CUDA JIT for non-linear 3D and 4D arrays
* OpenCL Backend
    * Improve compilation times for OpenCL backend
    * Performance improvements for non-linear JIT kernels on OpenCL
    * Improved shared memory load/store in many OpenCL kernels (PR 933)
    * Using cl.hpp v1.2.7

Bug Fixes
---------
* Common
    * Fix compatibility of c32/c64 arrays when operating with scalars
    * Fix median for all values of an array
    * Fix double free issue when indexing (30cbbc7)
    * Fix [bug](https://github.com/arrayfire/arrayfire/issues/901) in rank
    * Fix default values for scale throwing exception
    * Fix conjg raising exception on real input
    * Fix bug when using conjugate transpose for vector input
    * Fix issue with const input for array_proxy::get()
* CPU Backend
    * Fix randn generating same sequence for multiple calls
    * Fix setSeed for randu
    * Fix casting to and from complex
    * Check NULL values when allocating memory
    * Fix [offset issue](https://github.com/arrayfire/arrayfire/issues/923) for CPU element-wise operations

New Examples
------------
* Match Template
* Susan
* Heston Model (contributed by Michael Nowotny)

Installer
----------
* Fixed bug in automatic detection of ArrayFire when using with CMake in Windows
* The Linux libraries are now compiled with static version of FreeImage

Known Issues
------------
* OpenBlas can cause issues with QR factorization in CPU backend
* FreeImage older than 3.10 can cause issues with loadImageMem and
  saveImageMem
* OpenCL backend issues on OSX
    * AMD GPUs not supported because of driver issues
    * Intel CPUs not supported
    * Linear algebra functions do not work on Intel GPUs.
* Stability and correctness issues with open source OpenCL implementations such as Beignet, GalliumCompute.

v3.0.2
==============

Bug Fixes
--------------

* Added missing symbols from the compatible API
* Fixed a bug affecting corner rows and elements in \ref grad()
* Fixed linear interpolation bugs affecting large images in the following:
    - \ref approx1()
    - \ref approx2()
    - \ref resize()
    - \ref rotate()
    - \ref scale()
    - \ref skew()
    - \ref transform()

Documentation
-----------------

* Added missing documentation for \ref constant()
* Added missing documentation for `array::scalar()`
* Added supported input types for functions in `arith.h`

v3.0.1
==============

Bug Fixes
--------------

* Fixed header to work in Visual Studio 2015
* Fixed a bug in batched mode for FFT based convolutions
* Fixed graphics issues on OSX
* Fixed various bugs in visualization functions

Other improvements
---------------

* Improved fractal example
* New OSX installer
* Improved Windows installer
  * Default install path has been changed
* Fixed bug in machine learning examples

<br>

v3.0.0
=================

Major Updates
-------------

* ArrayFire is now open source
* Major changes to the visualization library
* Introducing handle based C API
* New backend: CPU fallback available for systems without GPUs
* Dense linear algebra functions available for all backends
* Support for 64 bit integers

Function Additions
------------------
* Data generation functions
    * range()
    * iota()

* Computer Vision Algorithms
    * features()
        * A data structure to hold features
    * fast()
        * FAST feature detector
    * orb()
        * ORB A feature descriptor extractor

* Image Processing
    * convolve1(), convolve2(), convolve3()
        * Specialized versions of convolve() to enable better batch support
    * fftconvolve1(), fftconvolve2(), fftconvolve3()
        * Convolutions in frequency domain to support larger kernel sizes
    * dft(), idft()
        * Unified functions for calling multi dimensional ffts.
    * matchTemplate()
        * Match a kernel in an image
    * sobel()
        * Get sobel gradients of an image
    * rgb2hsv(), hsv2rgb(), rgb2gray(), gray2rgb()
        * Explicit function calls to colorspace conversions
    * erode3d(), dilate3d()
        * Explicit erode and dilate calls for image morphing

* Linear Algebra
    * matmulNT(), matmulTN(), matmulTT()
        * Specialized versions of matmul() for transposed inputs
    * luInPlace(), choleskyInPlace(), qrInPlace()
        * In place factorizations to improve memory requirements
    * solveLU()
        * Specialized solve routines to improve performance
    * OpenCL backend now Linear Algebra functions

* Other functions
    * lookup() - lookup indices from a table
    * batchFunc() - helper function to perform batch operations

* Visualization functions
    * Support for multiple windows
    * window.hist()
        * Visualize the output of the histogram

* C API
    * Removed old pointer based C API
    * Introducing handle base C API
    * Just In Time compilation available in C API
    * C API has feature parity with C++ API
    * bessel functions removed
    * cross product functions removed
    * Kronecker product functions removed

Performance Improvements
------------------------
* Improvements across the board for OpenCL backend

API Changes
---------------------
* `print` is now af_print()
* seq(): The step parameter is now the third input
    * seq(start, step, end) changed to seq(start, end, step)
* gfor(): The iterator now needs to be seq()

Deprecated Function APIs
------------------------
Deprecated APIs are in af/compatible.h

* devicecount() changed to getDeviceCount()
* deviceset() changed to setDevice()
* deviceget() changed to getDevice()
* loadimage() changed to loadImage()
* saveimage() changed to saveImage()
* gaussiankernel() changed to gaussianKernel()
* alltrue() changed to allTrue()
* anytrue() changed to anyTrue()
* setunique() changed to setUnique()
* setunion() changed to setUnion()
* setintersect() changed to setIntersect()
* histequal() changed to histEqual()
* colorspace() changed to colorSpace()
* filter() deprecated. Use convolve1() and convolve2()
* mul() changed to product()
* deviceprop() changed to deviceProp()

Known Issues
----------------------
* OpenCL backend issues on OSX
    * AMD GPUs not supported because of driver issues
    * Intel CPUs not supported
    * Linear algebra functions do not work on Intel GPUs.
* Stability and correctness issues with open source OpenCL implementations such as Beignet, GalliumCompute.
