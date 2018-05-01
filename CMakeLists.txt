cmake_minimum_required(VERSION 3.2 FATAL_ERROR)
PROJECT(units LANGUAGES CXX)
set(units_VERSION 2.3.1)
message("Building units")

SET(CMAKE_CXX_STANDARD 14)
SET(CMAKE_CXX_STANDARD_REQUIRED TRUE)

# create and configure the library target
add_library(units INTERFACE)
target_include_directories(units INTERFACE include)

if("${CMAKE_CXX_COMPILER_ID}" STREQUAL "MSVC")
    # enable parallel build
    set( ENV{CL} /MP )
    target_compile_definitions(${PROJECT_NAME} INTERFACE "/permissive-")
elseif("${CMAKE_CXX_COMPILER_ID}" STREQUAL "GNU")
    # Increase warning levels
    add_compile_options(-Wall -Wextra -pedantic)
endif()