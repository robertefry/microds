
cmake_minimum_required(VERSION 3.12)
include(cmake/get_cpm.cmake)

project("microds" VERSION "0.1.0" LANGUAGES "C" "CXX"
  HOMEPAGE_URL "https://github.com/robertefry/microds"
  DESCRIPTION "Lightweight data structures for C++ embedded applications."
)

add_library(microds INTERFACE)

target_include_directories(microds INTERFACE
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
  $<INSTALL_INTERFACE:include>
)

enable_testing()
add_subdirectory(tests)
