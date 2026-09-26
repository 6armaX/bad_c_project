cmake_minimum_required(VERSION 3.16)

project(mathlib VERSION 0.4.0 LANGUAGES C)

# TODO: разобраться с типами сборок, пока хардкодим Release
set(CMAKE_BUILD_TYPE Release CACHE STRING "build type" FORCE)

add_compile_options(-Wall -Wextra)

set(CMAKE_C_STANDARD 11)
set(CMAKE_C_STANDARD_REQUIRED ON)

add_library(math_utils src/math_utils.c)
target_include_directories(math_utils PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/src)

add_executable(math_cli src/main.c)
target_link_libraries(math_cli PRIVATE math_utils)
