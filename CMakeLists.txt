cmake_minimum_required(VERSION 3.8)
project(stamped_msgs)

# Check if ROS2 environment is sourced
if(NOT DEFINED ENV{ROS_DISTRO})
  message(FATAL_ERROR "ROS2 environment is not sourced! Please run: source /opt/ros/jazzy/setup.bash")
endif()

# Default to C++17
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 17)
endif()

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# Find dependencies
find_package(ament_cmake REQUIRED)
find_package(rosidl_default_generators REQUIRED)
find_package(std_msgs REQUIRED)
find_package(builtin_interfaces REQUIRED)

# Define all message files
set(msg_files
  "msg/Bool.msg"
  "msg/BoolArray.msg"
  "msg/Byte.msg"
  "msg/ByteArray.msg"
  "msg/ByteMultiArray.msg"
  "msg/Char.msg"
  "msg/CharArray.msg"
  "msg/ColorRGBA.msg"
  "msg/ColorRGBAArray.msg"
  "msg/Duration.msg"
  "msg/DurationArray.msg"
  "msg/Empty.msg"
  "msg/Float32.msg"
  "msg/Float32Array.msg"
  "msg/Float32MultiArray.msg"
  "msg/Float64.msg"
  "msg/Float64Array.msg"
  "msg/Float64MultiArray.msg"
  "msg/Int16.msg"
  "msg/Int16Array.msg"
  "msg/Int16MultiArray.msg"
  "msg/Int32.msg"
  "msg/Int32Array.msg"
  "msg/Int32MultiArray.msg"
  "msg/Int64.msg"
  "msg/Int64Array.msg"
  "msg/Int64MultiArray.msg"
  "msg/Int8.msg"
  "msg/Int8Array.msg"
  "msg/Int8MultiArray.msg"
  "msg/String.msg"
  "msg/StringArray.msg"
  "msg/UInt16.msg"
  "msg/UInt16Array.msg"
  "msg/UInt16MultiArray.msg"
  "msg/UInt32.msg"
  "msg/UInt32Array.msg"
  "msg/UInt32MultiArray.msg"
  "msg/UInt64.msg"
  "msg/UInt64Array.msg"
  "msg/UInt64MultiArray.msg"
  "msg/UInt8.msg"
  "msg/UInt8Array.msg"
  "msg/UInt8MultiArray.msg"
)

# Generate messages
rosidl_generate_interfaces(${PROJECT_NAME}
  ${msg_files}
  DEPENDENCIES std_msgs builtin_interfaces
  ADD_LINTER_TESTS
)

# Export dependencies
ament_export_dependencies(rosidl_default_runtime)

ament_package()
