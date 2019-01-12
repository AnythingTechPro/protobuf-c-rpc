SET(PACKAGE protobuf-c-rpc)
SET(PACKAGE_NAME protobuf-c-rpc)
SET(PACKAGE_VERSION 1.0.1)

CMAKE_MINIMUM_REQUIRED(VERSION 3.2 FATAL_ERROR)
PROJECT(protobuf-c-rpc)

SET(CMAKE_CXX_STANDARD 11)
SET(CMAKE_CXX_STANDARD_REQUIRED ON)
SET(CMAKE_CXX_EXTENSIONS OFF)

# options
option(MSVC_STATIC_BUILD "MSVC_STATIC_BUILD" OFF)
option(BUILD_PROTO3 "BUILD_PROTO3" ON)

# using Visual Studio C++
IF(MSVC)
  SET(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} /wd4267 /wd4244")
  SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} /wd4267 /wd4244")
ENDIF()

get_filename_component(MAIN_DIR ${CMAKE_CURRENT_SOURCE_DIR} PATH)
SET(TEST_DIR ${MAIN_DIR}/t)

MESSAGE(${MAIN_DIR})

SET (PC_SOURCES
        ${MAIN_DIR}/protobuf-c-rpc/gsklistmacros.h
        ${MAIN_DIR}/protobuf-c-rpc/gskrbtreemacros.h
        ${MAIN_DIR}/protobuf-c-rpc/protobuf-c-rpc-client.c
        ${MAIN_DIR}/protobuf-c-rpc/protobuf-c-rpc-data-buffer.c
        ${MAIN_DIR}/protobuf-c-rpc/protobuf-c-rpc-data-buffer.h
        ${MAIN_DIR}/protobuf-c-rpc/protobuf-c-rpc-dispatch.c
        ${MAIN_DIR}/protobuf-c-rpc/protobuf-c-rpc-dispatch.h
        ${MAIN_DIR}/protobuf-c-rpc/protobuf-c-rpc-server.c
        ${MAIN_DIR}/protobuf-c-rpc/protobuf-c-rpc.h)

ADD_LIBRARY(protobuf-c-rpc ${PC_SOURCES})

INCLUDE_DIRECTORIES(${MAIN_DIR})
INCLUDE_DIRECTORIES(${MAIN_DIR}/protobuf-c-rpc)
INCLUDE_DIRECTORIES(${CMAKE_BINARY_DIR}) # for generated files
