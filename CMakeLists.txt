cmake_minimum_required(VERSION 3.8)

project(triangles LANGUAGES CXX)

set(CMAKE_CXX_STANDARD          20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS        OFF)

set(CMAKE_CXX_FLAGS_DEBUG "-Wall -Wextra -g -O0 -D DEBUG -fsanitize=address,alignment,bool,bounds,enum,float-cast-overflow,float-divide-by-zero,integer-divide-by-zero,leak,nonnull-attribute,null,object-size,return,returns-nonnull-attribute,shift,signed-integer-overflow,undefined,unreachable,vla-bound,vptr -lgtest -lgmock -pthread")
set(CMAKE_CXX_FLAGS_RELEASE "-Wall -O2 -DNDEBUG")

if(NOT CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE Release)
endif()

find_package(GTest REQUIRED)
enable_testing()

add_subdirectory(./src)
add_subdirectory(./test)

target_include_directories(triag     PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/inc/geometry)
target_include_directories(test_main PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/inc/geometry)

target_include_directories(triag     PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/inc)
target_include_directories(test_main PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/inc)
