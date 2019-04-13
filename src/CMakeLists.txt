cmake_minimum_required(VERSION 2.8)
project(ida_rpl_loader)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${CMAKE_SOURCE_DIR}/../cmake)

set(SOURCES
    tinfl.c
    loader.cpp
)

find_package(IDA)

include_directories(${IDA_INCLUDE_DIR})
include_directories(${IDA_SDK_PATH}/ldr)
include_directories(${ELF_COMMON_PATH})

add_definitions(${IDA_DEFINITIONS})

add_library(ida_rpl_loader SHARED ${SOURCES})
target_link_libraries(ida_rpl_loader ${IDA_LIBRARIES})
set_target_properties(ida_rpl_loader PROPERTIES OUTPUT_NAME "ida_rpl_loader" PREFIX "" SUFFIX "${IDA_PLUGIN_EXT}")