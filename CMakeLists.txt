cmake_minimum_required(VERSION 3.10)

project(HelloWorld)
set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
enable_testing()

find_package(fmt CONFIG REQUIRED)
find_package(GTest CONFIG REQUIRED)

add_executable(HelloWorld helloworld.cpp)

target_link_libraries(HelloWorld PRIVATE fmt::fmt)

add_executable(
  hello_test
  hello_test.cc
)
target_link_libraries(
  hello_test
  GTest::gtest_main
)
include(GoogleTest)
gtest_discover_tests(hello_test)