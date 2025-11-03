cmake_minimum_required(VERSION 3.12)
project(TerminalToys)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Add inih source files (minimal - just the C core)
set(INIH_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/inih/ini.c
)

set(INIH_HEADERS
    ${CMAKE_CURRENT_SOURCE_DIR}/inih/ini.h
)

# Include directories
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/inih)

# Example config reader executable
add_executable(example_config_reader
    example_config_reader.cpp
    ${INIH_SOURCES}
)

# If you want to create a library from inih for reuse
add_library(inih_lib STATIC
    ${INIH_SOURCES}
)

target_include_directories(inih_lib PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}/inih
)

