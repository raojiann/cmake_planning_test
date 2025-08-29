cmake_minimum_required(VERSION 3.29.0)
project(planning)
set(CMAKE_CXX_STANDARD 17)

# set output directory for executables and libraries
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/bin)

# source files
aux_source_directory(${PROJECT_SOURCE_DIR}/src SRC_LIST)

# build shared library
add_library(common
    SHARED
    ${SRC_LIST}
)

# include directory
target_include_directories(common
    PUBLIC
    ${PROJECT_SOURCE_DIR}/include
)

# build executable
add_executable(planning_main planning_main.cpp)

# link library
target_include_directories(planning_main
    PUBLIC
    ${PROJECT_SOURCE_DIR}/include
)

# link library
target_link_libraries(planning_main
    PUBLIC
    common
)