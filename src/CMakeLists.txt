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

###############################
###                         ###
###############################

configure_file(${CMAKE_SOURCE_DIR}/src/laplace.py ${CMAKE_BINARY_DIR}/src/laplace.py COPYONLY)
