cmake_minimum_required(VERSION 3.10)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -std=c++14")
set(CMAKE_CXX_FLAGS_RELEASE "${CMAKE_CXX_FLAGS_RELEASE} -O3")
set(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} -g -O0")

enable_testing()

project(test_cmake CXX)

add_executable(a.out main.cpp hello.cpp)

add_executable(unit_test unit_test.cc hello.cpp)

add_test(
  NAME hello_test # テスト名は hoge_test
  COMMAND $<TARGET_FILE:unit_test>
  # CONFIGURATIONS Release # テスト構成がReleaseのときのみ実行
  WORKING_DIRECTORY ${PROJECT_BINARY_DIR}
)