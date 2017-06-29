cmake_minimum_required(VERSION 2.8)

project(tinyxml)

if(NOT CMAKE_BUILD_TYPE AND NOT CMAKE_CONFIGURATION_TYPES)
  message(STATUS "Setting build type to 'Release' as none was specified.")
  set(CMAKE_BUILD_TYPE Release CACHE STRING "Choose the type of build." FORCE)
  set_property(CACHE CMAKE_BUILD_TYPE PROPERTY STRINGS "Debug" "Release" "MinSizeRel" "RelWithDebInfo")
endif()

option(BUILD_SHARED_LIBS "Build shared libraries" ON)
option(USE_STL "Compile using STL" ON)

add_library(tinyxml
  tinystr.cpp
  tinyxml.cpp
  tinyxmlerror.cpp
  tinyxmlparser.cpp
)

if (USE_STL)
  target_compile_definitions(tinyxml PRIVATE TIXML_USE_STL)
endif()

install(TARGETS tinyxml
  RUNTIME DESTINATION bin
  ARCHIVE DESTINATION lib
  LIBRARY DESTINATION lib
  FRAMEWORK DESTINATION "Library/Frameworks"
  PUBLIC_HEADER DESTINATION include
)
