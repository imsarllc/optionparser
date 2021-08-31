cmake_minimum_required(VERSION 3.13)

project(optionparser CXX)

set(CMAKE_CXX_STANDARD 11)

add_library(optionparser INTERFACE)
add_library(optionparser::optionparser ALIAS optionparser)

target_include_directories(optionparser
  INTERFACE include
  )

add_subdirectory(examples)
add_subdirectory(test)

add_custom_target(doc # not part of ALL target
  BYPRODUCTS nothing #this forces the target to always be out of date
  WORKING_DIRECTORY ${CMAKE_SOURCE_DIR}/doc
  COMMENT "Generating Doxygen docs"
  COMMAND doxygen
  COMMAND cat Doxyfile | sed '/^INTERNAL_DOCS/s/YES/NO/;/^HTML_OUTPUT/s/-dev//' | doxygen -
  )
  
