[![Appveyor build status (Windows)](https://ci.appveyor.com/api/projects/status/xfllw9vkp3lj4l0v/branch/main?svg=true)](https://ci.appveyor.com/project/ispc/ispc/branch/main)

Intel® Implicit SPMD Program Compiler (Intel® ISPC)
===================================================

``ispc`` is a compiler for a variant of the C programming language, with
extensions for
[single program, multiple data](http://en.wikipedia.org/wiki/SPMD)
programming.  Under the SPMD model,
the programmer writes a program that generally appears to be a regular
serial program, though the execution model is actually that a number of
*program instances* execute in parallel on the hardware.

Overview
--------

``ispc`` compiles a C-based SPMD programming language to run on the SIMD
units of CPUs and GPUs; it frequently provides a 3x or more speedup on architectures
with 4-wide vector SSE units and 5x-6x on architectures with 8-wide AVX vector units,
without any of the difficulty of writing intrinsics code.  Parallelization
across multiple cores is also supported by ``ispc``, making it
possible to write programs that achieve performance improvement that scales
by both number of cores and vector unit size.

There are a few key principles in the design of ``ispc``:

  * To build a small set of extensions to the C language that
    would deliver excellent performance to performance-oriented
    programmers who want to run SPMD programs on the CPU and GPU.

  * To provide a thin abstraction layer between the programmer
    and the hardware--in particular, to have an execution and
    data model where the programmer can cleanly reason about the
    mapping of their source program to compiled assembly language
    and the underlying hardware.

  * To make it possible to harness the computational power of SIMD
    vector units without the extremely low-programmer-productivity
    activity of directly writing intrinsics.

  * To explore opportunities from close coupling between C/C++
    application code and SPMD ``ispc`` code running on the
    same processor--to have lightweight function calls between
    the two languages and to share data directly via pointers without
    copying or reformatting.

``ispc`` is an open source compiler with the BSD license.  It uses the
remarkable [LLVM Compiler Infrastructure](http://llvm.org) for back-end
code generation and optimization and is [hosted on
github](http://github.com/ispc/ispc). It supports Windows, macOS, and
Linux as a host operating system and also capable to target Android, iOS,
and PS4/PS5.  It currently supports multiple flavours of x86 (SSE2,
SSE4, AVX, AVX2, and AVX512), ARM (NEON), and Intel® GPU architectures
(Gen9 and Xe family).

Features
--------

``ispc`` provides a number of key features to developers:

  * Familiarity as an extension of the C programming
    language: ``ispc`` supports familiar C syntax and
    programming idioms, while adding the ability to write SPMD
    programs.

  * High-quality SIMD code generation: the performance
    of code generated by ``ispc`` is often close to that of
    hand-written intrinsics code.

  * Ease of adoption with existing software
    systems: functions written in ``ispc`` directly
    interoperate with application functions written in C/C++ and
    with application data structures.
            
  * Portability across over a decade of CPU
    generations: ``ispc`` has targets for x86 SSE2, SSE4, AVX,
    AVX2, and AVX512, as well as ARM NEON and
    recent Intel® GPUs.

  * Portability across operating systems: Microsoft
    Windows, macOS, Linux, and FreeBSD are all supported
    by ``ispc``.

  * Debugging with standard tools: ``ispc``
    programs can be debugged with standard debuggers.

Additional Resources
--------------------

Prebuilt ``ispc`` binaries for Windows, macOS and Linux can be downloaded
from the [ispc downloads page](https://ispc.github.io/downloads.html).
Latest ``ispc`` binaries corresponding to main branch can be downloaded
from Appveyor for [Linux](https://ci.appveyor.com/api/projects/ispc/ispc/artifacts/build%2Fispc-trunk-linux.tar.gz?job=Environment%3A%20APPVEYOR_BUILD_WORKER_IMAGE%3DUbuntu1604%2C%20LLVM_VERSION%3Dlatest) and Windows ([msi](https://ci.appveyor.com/api/projects/ispc/ispc/artifacts/build%2Fispc-trunk-windows.msi?job=Environment%3A%20APPVEYOR_BUILD_WORKER_IMAGE%3DVisual%20Studio%202019%2C%20LLVM_VERSION%3Dlatest) or [zip](https://ci.appveyor.com/api/projects/ispc/ispc/artifacts/build%2Fispc-trunk-windows.zip?job=Environment%3A%20APPVEYOR_BUILD_WORKER_IMAGE%3DVisual%20Studio%202019%2C%20LLVM_VERSION%3Dlatest))
See also additional
[documentation](https://ispc.github.io/documentation.html) and additional
[performance information](https://ispc.github.io/perf.html).
If you have a bug report and have a question, you are welcome to open an [issue](https://github.com/ispc/ispc/issues) or start a [discussion](https://github.com/ispc/ispc/discussions) on GitHub.
