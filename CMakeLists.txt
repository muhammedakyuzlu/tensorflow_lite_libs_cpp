cmake_minimum_required(VERSION 3.0.0)
project(main)

set(CMAKE_CXX_STANDARD 14)

# include has 2 subdirectories: tensorflow and flatbuffers
INCLUDE_DIRECTORIES("[path/to/include/]")

# lib has 1 file: libtensorflowlite.so
ADD_LIBRARY(tensorflowlite SHARED IMPORTED)
set_property(TARGET tensorflowlite PROPERTY IMPORTED_LOCATION [path/to/libs/libtensorflowlite.so])

file(GLOB SOURCE_FILES src/*.cpp  src/*.h )
add_executable(${CMAKE_PROJECT_NAME} ${SOURCE_FILES})
target_link_libraries(main tensorflowlite)