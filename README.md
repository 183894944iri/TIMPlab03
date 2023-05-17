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
## Задание 3
Все первые пять пунктов для библиотеки `hello_world_application`
В CMakeLists.txt
```
cmake_minimum_required(VERSION 3.4)
project(hello_world)
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/../formatter_ex_lib formatter_ex_lib_dir)
add_executable(hello_world ${CMAKE_CURRENT_SOURCE_DIR}/hello_world.cpp)
target_include_directories(hello_world PUBLIC
${CMAKE_CURRENT_SOURCE_DIR}/../formatter_ex_lib
)
target_link_libraries(hello_world formatter_ex_lib)
```
> ![image](https://github.com/183894944iri/TIMPlab03/assets/113174903/4db11b68-93f7-4eb4-a2a6-d9a456fcef1c)

Все первые пять пунктов для библиотеки `solver_lib`. Исправляем ошибки ручками
В CMakeLists.txt
```
cmake_minimum_required(VERSION 3.4)
project(solver_lib)
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
add_library(solver_lib ${CMAKE_CURRENT_SOURCE_DIR}/solver.cpp)
```
Все первые пять пунктов для библиотеки `solver_application`
В CMakeLists.txt
```
cmake_minimum_required(VERSION 3.4)
project(solver)
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/../formatter_ex_lib formatter_ex_lib_dir)
add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/../solver_lib solver_lib_dir)
add_executable(solver ${CMAKE_CURRENT_SOURCE_DIR}/equation.cpp)
target_include_directories(formatter_ex_lib PUBLIC
${CMAKE_CURRENT_SOURCE_DIR}/../formatter_ex_lib
${CMAKE_CURRENT_SOURCE_DIR}/../solver_lib
)
target_link_libraries(solver formatter_ex_lib solver_lib)
```

> <img width="773" alt="image" src="https://github.com/183894944iri/TIMPlab03/assets/113174903/27360a6f-8589-4d26-b30a-7d2c78a08f19">> 
> <img width="377" alt="image" src="https://github.com/183894944iri/TIMPlab03/assets/113174903/f7c2669a-2fd3-4e60-95d7-8ce79285380e">


