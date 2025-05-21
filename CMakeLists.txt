cmake_minimum_required(VERSION 3.14)
 
set(This Example)
project(${This} C CXX)
 
set(CMAKE_C_STANDARD 99)
set(CMAKE_CXX_STANDARD 11)
 
include(FetchContent)
 
# Check if local googletest folder exists
if(EXISTS "${CMAKE_SOURCE_DIR}/googletest/CMakeLists.txt")
    message(STATUS "Using local googletest folder")
    add_subdirectory(googletest)
else()
    message(STATUS "Fetching googletest using FetchContent")
    FetchContent_Declare(
      googletest
      URL https://github.com/google/googletest/archive/refs/heads/main.zip
    )
    FetchContent_MakeAvailable(googletest)
endif()
 
enable_testing()
 
set(Headers 
    Example.hpp
)
set(Sources 
    Example.cpp 
)
 
add_library(${This} STATIC ${Sources} ${Headers})
 
# Let test folder handle its own linking
add_subdirectory(test)
