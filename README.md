# TIMPlab03
## Задание 1
1. mkdir formatter_lib
2. cd formatter_lib
3. wget https://raw.githubusercontent.com/tp-labs/lab03/master/formatter_lib/formatter.h
4. wget https://raw.githubusercontent.com/tp-labs/lab03/master/formatter_lib/formatter.cpp
5. nano CMakeLists.txt 
```
 cmake_minimum_required(VERSION 3.4)
 project(formatter_lib)
 set(CMAKE_CXX_STANDARD 11)
 set(CMAKE_CXX_STANDARD_REQUIRED ON)
 add_library(formatter_lib STATIC ${CMAKE_CURRENT_SOURCE_DIR}/formatter.cpp)
```
Проверка  
> cmake -B build

> cmake --build build

><img width="653" alt="image" src="https://github.com/183894944iri/TIMPlab03/assets/113174903/85e78ce2-9948-4c6c-9673-f7536f51f749">
 
## Задание 2
Все первые пять пунктов для библиотеки `formatter_ex_lib`
В CMakeLists.txt
```
cmake_minimum_required(VERSION 3.4)
project(formatter_ex_lib)
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/../formatter_lib formatter_lib_dir)
add_library(formatter_ex_lib STATIC ${CMAKE_CURRENT_SOURCE_DIR}/formatter_ex.cpp)
target_include_directories(formatter_ex_lib PUBLIC
${CMAKE_CURRENT_SOURCE_DIR}/../formatter_lib
)
target_link_libraries(formatter_ex_lib formatter_lib)
```
