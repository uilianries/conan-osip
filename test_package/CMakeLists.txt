cmake_minimum_required(VERSION 3.1)
project(conan-osip-test)

set(CMAKE_VERBOSE_MAKEFILE TRUE)

# Conan package ################################################################
include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
conan_basic_setup()

# Source files #################################################################
file(GLOB SOURCE_FILES src/*.c)

# Build application ############################################################
add_executable(${CMAKE_PROJECT_NAME} ${SOURCE_FILES})
set_property(TARGET ${CMAKE_PROJECT_NAME} PROPERTY C_STANDARD 99)
target_link_libraries(${CMAKE_PROJECT_NAME} ${CONAN_LIBS})

# Add test #####################################################################
enable_testing()
add_test(NAME test-all
         WORKING_DIRECTORY ${CMAKE_BINARY_DIR}/bin
         COMMAND ${PROJECT_NAME})
