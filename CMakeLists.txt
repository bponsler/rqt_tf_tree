cmake_minimum_required(VERSION 3.5)
project(rqt_tf_tree)

# Add support for C++11
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 11)
endif()

find_package(ament_cmake REQUIRED)
find_package(ament_cmake_python REQUIRED)

ament_python_install_package(${PROJECT_NAME})

set(INCLUDE_DIRS ${ament_cmake_INCLUDE_DIRS})
include_directories(${INCLUDE_DIRS})

set(LIBRARY_DIRS ${ament_cmake_LIBRARY_DIRS})

link_directories(${LIBRARY_DIRS})

set(LIBS ${ament_cmake_LIBRARIES})

# Load catkin and all dependencies required for this package

install(FILES plugin.xml DESTINATION share/${PROJECT_NAME})

install(DIRECTORY resource DESTINATION share/${PROJECT_NAME})

install(PROGRAMS scripts/rqt_tf_tree
  DESTINATION lib/${PROJECT_NAME})

ament_export_dependencies(ament_cmake)
ament_export_include_directories(${INCLUDE_DIRS})

ament_package()
