cmake_minimum_required(VERSION 3.10.2)
project(stamped_msgs)

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
