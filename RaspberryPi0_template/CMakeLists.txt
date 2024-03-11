cmake_minimum_required(VERSION 3.27.8)
project(HelloWorld)

# Set the cross-compiler
set(CMAKE_C_COMPILER "arm-none-eabi-gcc")
set(CMAKE_CXX_COMPILER "arm-none-eabi-g++")

# Set Raspberry Pi target architecture
set(CMAKE_SYSTEM_NAME "Linux")
set(CMAKE_SYSTEM_PROCESSOR "arm")

# Create executable
add_executable(hello helloworld.cpp)