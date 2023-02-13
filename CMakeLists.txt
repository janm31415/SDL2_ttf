if(${CMAKE_SOURCE_DIR} STREQUAL ${CMAKE_BINARY_DIR})
  message(FATAL_ERROR "Prevented in-tree built. Please create a build directory outside of the SDL_ttf source code and call cmake from there")
endif()

##### general #####
cmake_minimum_required(VERSION 3.0)
project(SDL_ttf C)

include(GNUInstallDirs)
include(CMakePackageConfigHelpers)

#find_package(SDL2 REQUIRED)
#find_package(Freetype REQUIRED)
#find_package(PkgConfig QUIET)

set(SDL_TTF_MAJOR_VERSION 2)
set(SDL_TTF_MINOR_VERSION 20)
set(SDL_TTF_MICRO_VERSION 2)
set(SDL_TTF_INTERFACE_AGE 0)
set(SDL_TTF_BINARY_AGE 14)
set(SDL_TTF_VERSION "${SDL_TTF_MAJOR_VERSION}.${SDL_TTF_MINOR_VERSION}.${SDL_TTF_MICRO_VERSION}")

##### library generation #####
add_library(SDL2_ttf SDL_ttf.c SDL_ttf.h)
target_link_libraries(SDL2_ttf SDL2 freetype)
target_include_directories(SDL2_ttf 
  PUBLIC 
  ${CMAKE_CURRENT_SOURCE_DIR}/../SDL2/include
  ${CMAKE_CURRENT_SOURCE_DIR}/../freetype/include
)