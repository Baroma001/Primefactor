cmake_minimum_required(VERSION 3.28)
project(Primefactor)

set(CMAKE_CXX_STANDARD 17)

# Specify the compilers explicitly
set(CMAKE_C_COMPILER "/usr/bin/clang")
set(CMAKE_CXX_COMPILER "/usr/bin/clang++")

# Find Boost library
find_package(Boost 1.81 REQUIRED COMPONENTS)

if(NOT Boost_FOUND)
    message(FATAL_ERROR "Boost not found! Install Boost and try again.")
endif()

# Add the executable target
add_executable(Primefactor main.cpp
        largeNumber.h
        largeNumber.cpp)

# Include Boost headers
target_include_directories(Primefactor PRIVATE ${Boost_INCLUDE_DIRS})

# Link Boost (for header-only libraries like multiprecision, linking is optional)
target_link_libraries(Primefactor Boost::boost)
