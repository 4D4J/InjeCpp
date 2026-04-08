cmake_minimum_required(VERSION 3.10.0)
project(UniversalDllInjector VERSION 0.1.0 LANGUAGES C CXX)

# Require C++17 at least
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# Define our source files
set(SOURCES
    src/code/dll_ejector.cpp
    src/code/dll_injector.cpp
    src/code/injector_main.cpp
    src/code/process_finder.cpp
    src/code/ui_controls.cpp
    src/code/ui_handlers.cpp
    src/code/ui_helpers.cpp
)

# Create an executable (WIN32 to hide the console window)
add_executable(injector WIN32 ${SOURCES})

# Add header include directory
target_include_directories(injector PRIVATE src/header)


