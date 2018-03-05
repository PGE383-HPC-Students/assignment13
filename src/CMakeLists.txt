find_package(PythonLibs REQUIRED)
include_directories(${PYTHON_INCLUDE_PATH})

find_package(NumPy REQUIRED)
include_directories(${PYTHON_NUMPY_INCLUDE_DIR})

find_package(SWIG REQUIRED)
include(${SWIG_USE_FILE})

add_library(iterate iterate.c)
set_property(TARGET iterate PROPERTY C_STANDARD 99)
target_include_directories(iterate PUBLIC ${CMAKE_SOURCE_DIR}/src)

include_directories(${CMAKE_SOURCE_DIR}/src)
swig_add_module(iterate python iterate.i)
swig_link_libraries(iterate iterate)
if(APPLE)
    swig_link_libraries(iterate "-undefined dynamic_lookup")
endif()

configure_file(${CMAKE_SOURCE_DIR}/src/laplace.py ${CMAKE_BINARY_DIR}/src/laplace.py COPYONLY)

INSTALL(FILES ${CMAKE_CURRENT_BINARY_DIR}/src/interate.py ${CMAKE_CURRENT_BINARY_DIR}/src/laplace.py DESTINATION ${CONDA_PREFIX}/lib/python3.6/site-packages/laplace)
INSTALL(TARGETS iterate DESTINATION ${CONDA_PREFIX}/lib/python3.6/site-packages/laplace)
