cmake_minimum_required(VERSION 3.13)

add_executable(example EXCLUDE_FROM_ALL)
add_executable(example_arg EXCLUDE_FROM_ALL)

target_link_libraries(example PRIVATE optionparser)
target_link_libraries(example_arg PRIVATE optionparser)

target_sources(example PRIVATE
  example.cpp
  )

target_sources(example_arg PRIVATE
  example_arg.cc
  )
