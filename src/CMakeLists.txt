find_package(PythonLibs REQUIRED)
include_directories(${PYTHON_INCLUDE_PATH})

find_package(NumPy REQUIRED)
include_directories(${PYTHON_NUMPY_INCLUDE_DIR})

cmake_policy(SET CMP0078 NEW)
cmake_policy(SET CMP0086 NEW)
find_package(SWIG REQUIRED)
include(${SWIG_USE_FILE})

###############################
### Add CMake commands here ###
###############################
add_library(iterate iterate.c)
#set_property(TARGET iterate PROPERTY C_STANDARD 99)
target_include_directories(iterate PUBLIC ${CMAKE_SOURCE_DIR}/src)

include_directories(${CMAKE_SOURCE_DIR}/src)
swig_add_library(_iterate TYPE MODULE LANGUAGE python SOURCES iterate.i)
swig_link_libraries(_iterate iterate)
###############################
###                         ###
###############################

configure_file(${CMAKE_SOURCE_DIR}/src/laplace.py ${CMAKE_BINARY_DIR}/src/laplace.py COPYONLY)
