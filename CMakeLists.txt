cmake_minimum_required(VERSION 3.22)

project(halx_dynamixel LANGUAGES CXX)

# halx_dynamixel
add_library(${PROJECT_NAME} OBJECT
  DynamixelSDK/c++/src/dynamixel_sdk/group_bulk_read.cpp
  DynamixelSDK/c++/src/dynamixel_sdk/group_bulk_write.cpp
  DynamixelSDK/c++/src/dynamixel_sdk/group_sync_read.cpp
  DynamixelSDK/c++/src/dynamixel_sdk/group_sync_write.cpp
  DynamixelSDK/c++/src/dynamixel_sdk/group_fast_bulk_read.cpp
  DynamixelSDK/c++/src/dynamixel_sdk/group_fast_sync_read.cpp
  DynamixelSDK/c++/src/dynamixel_sdk/group_handler.cpp
  DynamixelSDK/c++/src/dynamixel_sdk/packet_handler.cpp
  DynamixelSDK/c++/src/dynamixel_sdk/protocol1_packet_handler.cpp
  DynamixelSDK/c++/src/dynamixel_sdk/protocol2_packet_handler.cpp
  src/port_handler.cpp
)
target_link_libraries(${PROJECT_NAME} PUBLIC
  halx
)
target_include_directories(${PROJECT_NAME} PUBLIC
  DynamixelSDK/c++/include/dynamixel_sdk
  include
)
target_compile_definitions(${PROJECT_NAME} PUBLIC
  ARDUINO
)
