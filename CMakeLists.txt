cmake_minimum_required(VERSION 3.16)
project(pid_controller
    VERSION 1.0.0
    DESCRIPTION "Inverted pendulum PID controller simulation"
    LANGUAGES CXX
)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

add_compile_options(
    -Wall
    -Wextra
    -Wpedantic
    -Wshadow
    -Wconversion
    -Wsign-conversion
)

add_library(pid_core STATIC
    src/Pendulum.cpp
    src/PIDController.cpp
    src/Simulation.cpp
)

target_include_directories(pid_core PUBLIC include)

add_executable(pid_sim app/main.cpp)
target_link_libraries(pid_sim PRIVATE pid_core)

add_subdirectory(tests)
