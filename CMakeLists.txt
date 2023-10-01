cmake_minimum_required(VERSION 3.5)

project(helloworld VERSION 1.0.0 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_AUTOUIC ON)

if(CMAKE_VERSION VERSION_LESS "3.7.0")
    set(CMAKE_INCLUDE_CURRENT_DIR ON)
endif()

find_package(Qt5 COMPONENTS Widgets REQUIRED)

add_executable(helloworld
    src/test.cpp
)

target_link_libraries(helloworld Qt5::Widgets)

# set target properties
set_target_properties(
    helloworld 
    PROPERTIES
    CXX_STANDARD 17
    CXX_STANDARD_REQUIRED ON
)



if (MSVC)
    target_compile_options(
        helloworld PRIVATE
        /W4
    )
else ()
    target_compile_options(
        helloworld PRIVATE
        -Wall -Wextra -pedantic -Werror
    )
endif()


