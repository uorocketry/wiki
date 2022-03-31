---
title: Unit Tests
description: 
published: true
date: 2022-03-31T12:36:21.864Z
tags: 
editor: markdown
dateCreated: 2022-02-28T22:32:26.619Z
---

# Creating Unit Tests

We are using the Catch2 framework for writing unit tests. This allows a simple and straightforward way to write and run unit tests.

## Writing simple unit tests

In the root of the rocket code, you should see a folder called `unitTesting`. All unit tests should go in this folder. For adding new tests, first check if the tests would fit in an existing file. If not, simply create a new file. Ideally, we should separate the tests such that each file only covers one specific component or class. For example, testing the state machine would go in one file, testing the interface would go in another one, etc.

When creating a new test file, simply give it a name and use the `.cpp` extension. For example, the file could be named `foo.cpp`. After creating the file, include the Catch2 header: `#include <catch2/catch.hpp>`.

Next, we can write some unit tests. Here is an example taken from the Catch2 documentation:
```c++
#include <catch2/catch.hpp>

unsigned int Factorial( unsigned int number ) {
    return number <= 1 ? number : Factorial(number-1)*number;
}

TEST_CASE( "Factorials are computed", "[factorial]" ) {
    REQUIRE( Factorial(1) == 1 );
    REQUIRE( Factorial(2) == 2 );
    REQUIRE( Factorial(3) == 6 );
    REQUIRE( Factorial(10) == 3628800 );
}
```

Obviously, the code that you will write will test the rocket code, but the above is a nice simple example. Here are the main points to take from it:
  - We first have the `TEST_CASE` macro. The first argument is a unique test name, and the second argument is one or more optional tags. Tags allow an easy way to run a specific subset of the tests by specifying the tag name.
  - We also have the `REQUIRE` macro. Those lines are the actual tests and make assertions on what the code should return.

And we are done! We are now ready to run our simple tests. Note that Catch2 has way more features than this. See the [Catch2 documentation](https://github.com/catchorg/Catch2/blob/devel/docs/tutorial.md) on how to write more advanced tests.

## Running the unit tests
To run the tests, simply run the `unitTest.sh` script and you should see the test results.

In the background, the `unitTest.sh` script builds the target `tests` which only contains the unit tests. The output of this is the executable `./build/unitTesting/tests`. To run the unit tests, we simply run this executable.