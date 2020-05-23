cmake_minimum_required(VERSION 3.2...3.17)

project(FastNoise VERSION 0.4.0
    DESCRIPTION "FastNoise is an open source noise generation library with a large collection of different noise algorithms."
    LANGUAGES CXX
)

option(FASTNOISE_USE_DOUBLES "use doubles throughout FastNoise instead of floats" OFF)

add_library(${PROJECT_NAME} src/FastNoise.cpp include/FastNoise.h)

if(FASTNOISE_USE_DOUBLES)
    target_compile_definitions(FastNoise PUBLIC FN_USE_DOUBLES)
endif()

target_include_directories(${PROJECT_NAME} 
    PUBLIC 
        $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
        $<INSTALL_INTERFACE:include>
    PRIVATE 
        src
)


