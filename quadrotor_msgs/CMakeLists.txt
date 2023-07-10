cmake_minimum_required(VERSION 3.14.0)
project(quadrotor_msgs)

# Compile as C++11, supported in ROS Kinetic and newer
add_compile_options(-std=c++11)
add_compile_options(-O3)

find_package(catkin REQUIRED COMPONENTS geometry_msgs message_generation
                                        nav_msgs std_msgs)
file(
  GLOB_RECURSE MSG_FILES
  RELATIVE "${CMAKE_CURRENT_SOURCE_DIR}/msg"
  "*.msg")

add_message_files(FILES ${MSG_FILES})

generate_messages(DEPENDENCIES geometry_msgs nav_msgs std_msgs)

catkin_package()
