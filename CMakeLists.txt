# CMake standard commands
cmake_minimum_required(VERSION 3.10)
set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON) # enforces C++ version match

project(sfml-app VERSION 1.0)

file(GLOB_RECURSE SRC_FILES src/*.cpp) # recursively search for all .cpp files and store into specified variable

set(SFML_INCLUDE_DIR /usr/local/Cellar/sfml/2.5.1/include) # include path for SFML - contains all headers (.hpp) - required by compiler
# Usually /usr/local/<...> if installed via some package manager

set(CMAKE_INSTALL_RPATH_USE_LINK_PATH TRUE) # config for dynamic libraries
link_directories(/usr/local/Cellar/sfml/2.5.1/lib) # specify lib path to look for SFML - contains all dynamic library files (.dll, dylib, .so) - required by linker
# Standard path

add_executable(sfml-app ${SRC_FILES})
target_include_directories(sfml-app PUBLIC include ${SFML_INCLUDE_DIR}) # include -> folder in project root dir
target_link_libraries(sfml-app PUBLIC sfml-graphics sfml-window sfml-system sfml-audio sfml-network) # link sfml-graphics dynamic link library file (libsfml-sfml-graphics.dylib in MacOS), and others to sfml-app executable