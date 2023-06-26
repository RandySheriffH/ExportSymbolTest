cmake_minimum_required(VERSION 3.19)
project(export_symbol_test)

if(WIN32)
  set(CMAKE_WINDOWS_EXPORT_ALL_SYMBOLS ON)
endif()

add_executable(main ../main.cc)
add_library(foo SHARED ../foo.cc)

if(WIN32)
  target_link_libraries(main PRIVATE RelWithDebInfo/foo)
else()
  target_link_libraries(main PRIVATE foo)
endif()
