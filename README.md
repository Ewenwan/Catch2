<a id="top"></a>
![catch logo](artwork/catch2-logo-small.png)

[![Github Releases](https://img.shields.io/github/release/catchorg/catch2.svg)](https://github.com/catchorg/catch2/releases)
[![Build Status](https://travis-ci.org/catchorg/Catch2.svg?branch=master)](https://travis-ci.org/catchorg/Catch2)
[![Build status](https://ci.appveyor.com/api/projects/status/github/catchorg/Catch2?svg=true)](https://ci.appveyor.com/project/catchorg/catch2)
[![codecov](https://codecov.io/gh/catchorg/Catch2/branch/master/graph/badge.svg)](https://codecov.io/gh/catchorg/Catch2)
[![Try online](https://img.shields.io/badge/try-online-blue.svg)](https://wandbox.org/permlink/p9Pcgple8QWwgNR0)
[![Join the chat in Discord: https://discord.gg/4CWS9zD](https://img.shields.io/badge/Discord-Chat!-brightgreen.svg)](https://discord.gg/4CWS9zD)


<a href="https://github.com/catchorg/Catch2/releases/download/v2.11.3/catch.hpp">The latest version of the single header can be downloaded directly using this link</a>


Catch2是及其简单的C++测试框架，与gtest，boost.test和CppUnit相比Catch2非常小，甚至你只需要一个头文件就可以轻松的使用了。在小型项目里面可以很方便的用它搭建测试框架，同时配合一个更为简单的打桩框架[stub]()，分分钟让你的测试用例跑起来。

获取
有两种方法获取Catch2：
一种是直接下载头文件catch.hpp——推荐使用这种方式，可以简单的融入你的项目。
另一种是，获取catch2源码，https://github.com/catchorg/Catch2.git 适合二次开发或者学习里面的demo。


> 开启examples编译

    (base) frank@deepin:~/git/Catch2$ mkdir build
    (base) frank@deepin:~/git/Catch2$ cd build/
    (base) frank@deepin:~/git/Catch2/build$ cmake -DCATCH_BUILD_EXAMPLES=ON ../
    -- The CXX compiler identification is GNU 9.2.0
    -- Check for working CXX compiler: /usr/local/bin/c++
    -- Check for working CXX compiler: /usr/local/bin/c++ -- works
    -- Detecting CXX compiler ABI info
    -- Detecting CXX compiler ABI info - done
    -- Detecting CXX compile features
    -- Detecting CXX compile features - done
    -- Found PythonInterp: /home/frank/miniconda3/bin/python (found version "3.7.4") 
    -- Examples included
    -- Configuring done
    -- Generating done
    -- Build files have been written to: /home/frank/git/Catch2/build
    (base) frank@deepin:~/git/Catch2/build$ make -j4


 先从一个最简单的例子开始。
 
 ```c
#define CATCH_CONFIG_MAIN  // 这个宏定义了catch的main函数

// Standard C/C++ main entry point
//int main (int argc, char * argv[]) {
//    return Catch::Session().run( argc, argv );
//}

#include <catch2/catch.hpp> // 引入catch2，头文件，这里用的是"<...>"   也可能是 "catch2/catch.hpp"

// 是被测函数
int Factorial( int number ) {
   return number <= 1 ? number : Factorial( number - 1 ) * number;  // fail
// return number <= 1 ? 1      : Factorial( number - 1 ) * number;  // pass
}

TEST_CASE( "Factorial of 0 is 1 (fail)", "[single-file]" ) {
    REQUIRE( Factorial(0) == 1 );
}

TEST_CASE( "Factorials of 1 and higher are computed (pass)", "[single-file]" ) {
    REQUIRE( Factorial(1) == 1 );
    REQUIRE( Factorial(2) == 2 );
    REQUIRE( Factorial(3) == 6 );
    REQUIRE( Factorial(10) == 3628800 );

```

## Catch2 is released!

If you've been using an earlier version of Catch, please see the
Breaking Changes section of [the release notes](https://github.com/catchorg/Catch2/releases/tag/v2.0.1)
before moving to Catch2. You might also like to read [this blog post](https://levelofindirection.com/blog/catch2-released.html) for more details.

## What's the Catch?

Catch2 is a multi-paradigm test framework for C++. which also supports
Objective-C (and maybe C).
It is primarily distributed as a single header file, although certain
extensions may require additional headers.

## How to use it
This documentation comprises these three parts:

* [Why do we need yet another C++ Test Framework?](docs/why-catch.md#top)
* [Tutorial](docs/tutorial.md#top) - getting started
* [Reference section](docs/Readme.md#top) - all the details

## More
* Issues and bugs can be raised on the [Issue tracker on GitHub](https://github.com/catchorg/Catch2/issues)
* For discussion or questions please use [the dedicated Google Groups forum](https://groups.google.com/forum/?fromgroups#!forum/catch-forum) or our [Discord](https://discord.gg/4CWS9zD)
* See [who else is using Catch2](docs/opensource-users.md#top)
