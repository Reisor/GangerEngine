cmake_minimum_required(VERSION 2.8.7)
project("Ganger Engine")

# Set the library type to Shared
SET (LIB_TYPE SHARED)

if(CMAKE_COMPILER_IS_GNUCXX)
    set(CMAKE_CXX_FLAGS "${CMAKE_CSS_FLAGS} -std=c++11")
elseif(CMAKE_CXX_COMPILER_ID STREQUAL "Clang")
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -stdlib=libc++")
    add_definitions(-DEFGE_USE_STD_RANDOMENGINE)
endif()

set(SDL_HEADERS ${CMAKE_SOURCE_DIR}/libs)
set(SOURCES
  src/Errors.cpp
  src/GLSLProgram.cpp
  src/ImageLoader.cpp
  src/IOManager.cpp
  src/PicoPNG.cpp
  src/ResourceManager.cpp
  src/Sprite.cpp
  src/TextureCache.cpp)

#Bring the headers into the project
include_directories(${CMAKE_SOURCE_DIR}/libs ${CMAKE_SOURCE_DIR}/include)

#However, the file(GLOB...) allows for wildcard additions:
#file(GLOB SOURCES "src/*.cpp" ${SDL_HEADERS})

add_library(GangerEngine ${SOURCES} ${SDL_HEADERS})