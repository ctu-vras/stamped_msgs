cmake_minimum_required(VERSION 3.10.2)
project(stamped_msgs)

find_package(ament_cmake QUIET)
find_package(catkin QUIET)

if(catkin_FOUND)
  ## ROS 1 build
  set(MESSAGE_DEPS
    std_msgs
  )

  find_package(catkin REQUIRED COMPONENTS
    message_generation
    ${MESSAGE_DEPS}
  )

  add_message_files(
    FILES
    Bool.msg
    BoolArray.msg
    Byte.msg
    ByteArray.msg
    ByteMultiArray.msg
    Char.msg
    CharArray.msg
    ColorRGBA.msg
    ColorRGBAArray.msg
    Duration.msg
    DurationArray.msg
    Empty.msg
    Float32.msg
    Float32Array.msg
    Float32MultiArray.msg
    Float64.msg
    Float64Array.msg
    Float64MultiArray.msg
    Int16.msg
    Int16Array.msg
    Int16MultiArray.msg
    Int32.msg
    Int32Array.msg
    Int32MultiArray.msg
    Int64.msg
    Int64Array.msg
    Int64MultiArray.msg
    Int8.msg
    Int8Array.msg
    Int8MultiArray.msg
    String.msg
    StringArray.msg
    UInt16.msg
    UInt16Array.msg
    UInt16MultiArray.msg
    UInt32.msg
    UInt32Array.msg
    UInt32MultiArray.msg
    UInt64.msg
    UInt64Array.msg
    UInt64MultiArray.msg
    UInt8.msg
    UInt8Array.msg
    UInt8MultiArray.msg
  )

  generate_messages(DEPENDENCIES ${MESSAGE_DEPS})

  catkin_package(
    CATKIN_DEPENDS message_runtime ${MESSAGE_DEPS}
  )
elseif(ament_cmake_FOUND)
  ## ROS 2 build

  find_package(ament_cmake REQUIRED)
  find_package(rosidl_default_generators REQUIRED)
  find_package(std_msgs REQUIRED)
  find_package(builtin_interfaces REQUIRED)

  # Duration.msg and DurationArray.msg use builtin_interfaces/Duration in ROS 2 (msg_ros2/)
  # instead of the primitive 'duration' type used in ROS 1 (msg/)
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
    "${CMAKE_CURRENT_SOURCE_DIR}/msg_ros2:msg/Duration.msg"
    "${CMAKE_CURRENT_SOURCE_DIR}/msg_ros2:msg/DurationArray.msg"
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

  rosidl_generate_interfaces(${PROJECT_NAME}
    ${msg_files}
    DEPENDENCIES std_msgs builtin_interfaces
    ADD_LINTER_TESTS
  )

  ament_export_dependencies(rosidl_default_runtime)

  ament_package()
else()
  message(FATAL_ERROR "Neither catkin nor ament_cmake found.")
endif()
