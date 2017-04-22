cmake_minimum_required(VERSION 3.0)
project(Carabiner)

include(link/AbletonLinkConfig.cmake)
add_subdirectory(gflags)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -pthread -O2 -mcpu=cortex-a53 -mfpu=neon-fp-armv8 -mfloat-abi=hard")

set(mongoose_HEADERS
  mongoose.h
)

set(mongoose_SOURCES
  mongoose.c
)

add_executable(Carabiner
  ${mongoose_HEADERS}
  ${mongoose_SOURCES}
  carabiner.cpp
)

target_link_libraries(Carabiner Ableton::Link gflags)
