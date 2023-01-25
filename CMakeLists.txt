cmake_minimum_required(VERSION 3.11)

project(grpc_java_plugin)

set(CMAKE_CXX_STANDARD 14)

add_subdirectory(3rdparty/grpc)

file(GLOB JAVA_PLUGIN_SRCS ${CMAKE_CURRENT_SOURCE_DIR}/java_plugin.cpp
                           ${CMAKE_CURRENT_SOURCE_DIR}/java_generator.cpp
                           ${CMAKE_CURRENT_SOURCE_DIR}/java_generator.h)

add_executable(${PROJECT_NAME} ${JAVA_PLUGIN_SRCS})

target_include_directories(${PROJECT_NAME} PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/grpc/include)
target_include_directories(${PROJECT_NAME} PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/grpc/third_party/protobuf/src/)

target_link_libraries(${PROJECT_NAME} PRIVATE libprotobuf-lite grpc libprotoc)
