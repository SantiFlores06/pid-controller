add_executable(test_pid test_pid.cpp)
target_link_libraries(test_pid PRIVATE pid_core)
target_include_directories(test_pid PRIVATE ${CMAKE_SOURCE_DIR}/include)
