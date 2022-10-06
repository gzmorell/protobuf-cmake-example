cmake_minimum_required(VERSION 3.10.0)
project(addressbook)

set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

set(CMAKE_CXX_FLAGS "-g -Wall -Werror -std=c++17")

find_package(Protobuf REQUIRED)
include_directories(${Protobuf_INCLUDE_DIRS})
include_directories(${CMAKE_CURRENT_BINARY_DIR})

protobuf_generate_cpp(PROTO_SRCS PROTO_HRDS DESCRIPTORS PROTO_DESCS proto/addressbook.proto)
add_library(addressbook OBJECT ${PROTO_SRCS} ${PROTO_HDRS})
set_property(TARGET addressbook PROPERTY POSITION_INDEPENDENT_CODE 1)

add_library(addressbook_shared SHARED $<TARGET_OBJECTS:addressbook>)
set_target_properties(addressbook_shared PROPERTIES OUTPUT_NAME addressbook)

add_library(addressbook_static STATIC $<TARGET_OBJECTS:addressbook>)
set_target_properties(addressbook_static PROPERTIES OUTPUT_NAME addressbook)

add_subdirectory(src)