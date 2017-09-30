# Tomorrow's C++, Today

This is my repo for playing with super-modern stuff.

# What am I doing?

Not sure yet. I have a toybox, but no vision.

# What am I playing with?

## Networking TS

[N4656](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/n4656.pdf) is the working paper for
delivering low-level networking primitives to C++20. It is based upon the [Asio](http://think-async.com/Asio)
library, with a long history of development and implementation experience.

* https://github.com/chriskohlhoff/networking-ts-impl

## Ranges TS

[N4671](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/n4671.pdf) is the working paper for
the basis of the range-based second version of the C++ STL, contrasting with the iterator-based STL.

* https://github.com/ericniebler/range-v3
* https://github.com/Microsoft/Range-V3-VS2015

## Executors

Although there are already-published and in-development TSs relating to concurrent and parallel programming
such as the [Networking TS](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/n4656.pdf),
the [Parallelism TS](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4507.pdf) (mostly merged into C++17),
the [Concurrency TS](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0159r0.html), and (to a lesser extent)
the [Coroutines TS](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/n4663.pdf), along with the C++11-standardised
[`std::async(std::launch::async, ...)`](http://en.cppreference.com/w/cpp/thread/async), there has been a rather glaring
hole in them all, when it comes to "What does the hardware actually do?".

The answer has generally been either "Something like [`std::thread`](http://en.cppreference.com/w/cpp/thread/thread)" or
"implementation defined", deferring resolution upon the idea of 'Executors', and hence deferring merging things
such as `std::future::then` or the Paralellism TS's dynamic execution policies.

Helpfully, a second iteration of a 'Unified Executors Proposal'
([unpublished design P0761R0](https://github.com/executors/issaquah_2016/blob/R3/explanatory.md) and
[unpublished wording revision P0443R2](https://github.com/executors/issaquah_2016/blob/R3/wording.md))
has produced a prototype, which should allow experimenting with `std::future::then` at least, and
more-interesting `std::async` behaviours.

* https://github.com/executors/issaquah_2016/tree/R3

## Guideline Support Library

Although not *strictly* a C++-of-the-future thing, it's a core and evolving
[part](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#S-gsl) of
the idioms described in the [C++ Core Guidelines](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines).

* https://github.com/Microsoft/GSL
* If I need it, https://github.com/martinmoene/gsl-lite

## Catch

Again, not C++-of-the-future, but it is Catch of the future, and with a blurry enough screen you could
confuse the two.

Also, if I'm writing code, I'm writing tests. And if I'm writing tests in C++, I'm using Catch. And I wanted
a place to try-out the "catch2" branch of Catch, which should lead to Catch 2.0

* https://github.com/philsquared/Catch/tree/catch2

# What am I using to play with it?

aka "What do I need to set up", and "What other technologies am I trying to get better at?"

* (Modern) [CMake](https://cmake.org/)
* [git submodules](https://git-scm.com/book/en/v2/Git-Tools-Submodules)
* [Ninja](https://ninja-build.org/)

## MSYS2

http://www.msys2.org/

* [gcc 7.1](https://github.com/Alexpux/MINGW-packages/tree/master/mingw-w64-gcc)
* [clang 4.0](https://github.com/Alexpux/MINGW-packages/tree/master/mingw-w64-clang)

## MS Visual Studio

* VS 2017 C1/C2 (v141 toolchain)
* VS 2017 Clang/C2 (v141\_clang\_c2 toolchain)

I expect these will be [MSVC 2017 15.3](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-preview-relnotes) once it's released.

I plan to be able to use the MSVC CMake support, with CMake-Server.

## Linux

Unsure yet. At work, our Linux hosts are CentOS 7 w/devtoolset-6, which means gcc 6.2.1.

I don't yet know if that'll be modern-enough but I fear it won't be. So it may
be the [WSL](https://msdn.microsoft.com/commandline/wsl/about) with [Ubuntu 16.04](http://releases.ubuntu.com/16.04/)
and [gcc 7.1](https://launchpad.net/~ubuntu-toolchain-r/+archive/ubuntu/test?field.series_filter=xenial) and
[clang 4.0](http://apt.llvm.org/) at home, and possibly some kind of [Docker](https://www.docker.com/) container
with matching configuration on one of the Docker sandbox hosts at work.
