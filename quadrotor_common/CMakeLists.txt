cmake_minimum_required(VERSION 3.14.0)
project(quadrotor_common)

# Compile as C++11, supported in ROS Kinetic and newer
add_compile_options(-std=c++11)
add_compile_options(-O3)

find_package(Eigen3 REQUIRED)
find_package(catkin REQUIRED COMPONENTS roscpp geometry_msgs nav_msgs
                                        quadrotor_msgs)

catkin_package(
  INCLUDE_DIRS
  include
  LIBRARIES
  ${PROJECT_NAME}
  CATKIN_DEPENDS
  roscpp
  geometry_msgs
  nav_msgs
  quadrotor_msgs
  DEPENDS
  Eigen3)

add_library(
  ${PROJECT_NAME}
  src/control_command.cpp
  src/geometry_eigen_conversions.cpp
  src/math_common.cpp
  src/parameter_helper.cpp
  src/quad_state_estimate.cpp
  src/quaternion_functions.cpp
  src/trajectory_point.cpp
  src/trajectory.cpp)
target_include_directories(${PROJECT_NAME} PUBLIC include
                                                  ${catkin_INCLUDE_DIRS})
target_link_libraries(${PROJECT_NAME} PUBLIC Eigen3::Eigen ${catkin_LIBRARIES})
