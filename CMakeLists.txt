cmake_minimum_required(VERSION 3.23)
project(CoinConanTest)

##### SETs
set (CMAKE_BUILD_TYPE Release) 
set (CMAKE_CXX_STANDARD 20)
set (BUILD_SHARED_LIBS On)

##### Additional packages 

find_package (coin-cbc REQUIRED)

##### Include Dirs 

include_directories(
    SYSTEM
    includes
    "${PROJECT_BINARY_DIR}"
    )

##### Compile options 

add_compile_options(-Wall
    -DIL_STD
    -Wfatal-errors
    -pedantic
    -fopenmp
    -DDEBUG
    -fdiagnostics-color=always
    #    -Wall
    -lz
    -std=c++20
    #
    -lm 
    -lpthread 
    -ldl
    -Wno-sign-compare
    )

file(GLOB_RECURSE SOURCES "src/*.cpp")

add_executable(
    main 
    ${SOURCES} 
    )
    

target_link_libraries(
    main 
    coin-cbc::coin-cbc
    pthread 
    m 
    dl
    )
