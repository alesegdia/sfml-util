set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++0x")

file(GLOB_RECURSE CORE_SRC lib/core/*)

# set(SFML_STATIC_LIBRARIES TRUE)

find_package(SFML 2 COMPONENTS system window graphics network audio)
find_package(OpenGL REQUIRED)

add_library(sfmlutil ${CORE_SRC})

include_directories(sfmlutil lib)

if(OPENGL_FOUND AND SFML_FOUND AND BOX2D_FOUND)
	include_directories(${OPENGL_INCLUDE_DIR})
	include_directories(${SFML_INCLUDE_DIR})
endif()

set(EXECUTABLE_OUTPUT_PATH ${CMAKE_HOME_DIRECTORY}/bin)
set(LIBRARY_OUTPUT_PATH ${CMAKE_HOME_DIRECTORY}/lib)

