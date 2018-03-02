cmake_minimum_required (VERSION 2.6)
project (CMakeTest)
include_directories(
    .
    )
add_subdirectory(B buildB)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY bin)
execute_process(
	COMMAND python3 preparing.py
	WORKING_DIRECTORY A
	)
add_library(MyA STATIC "A/index.cpp")
add_executable(mytest "C/main.cpp")
target_link_libraries(mytest MyA)
target_link_libraries(mytest MyB)
