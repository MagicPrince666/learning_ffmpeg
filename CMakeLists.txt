CMAKE_MINIMUM_REQUIRED(VERSION 3.1)
SET(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${CMAKE_CURRENT_SOURCE_DIR}/cmake)
option(EXAMPLE "shall we complie example" on)
#INCLUDE(build_for_host)

include_directories(${CMAKE_SOURCE_DIR})

PROJECT(Decoder)

# SET(CMAKE_BUILD_TYPE "Debug")
SET(CMAKE_BUILD_TYPE "Release")

SET(CMAKE_C_FLAGS_DEBUG "${CMAKE_C_FLAGS} -O0 -Wall -g")
SET(CMAKE_C_FLAGS_RELEASE "${CMAKE_C_FLAGS} -Os -Wall")

SET(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS} -std=c++14 -O0 -Wall -g")
SET(CMAKE_CXX_FLAGS_RELEASE "${CMAKE_CXX_FLAGS} -std=c++14 -Os -Wall")

MESSAGE(STATUS ${CMAKE_SYSTEM_NAME})


#add_subdirectory(arch)

set(EXEC_NAME decoder)

add_executable(${EXEC_NAME} main.cpp

)

target_link_libraries(${EXEC_NAME}
    pthread
    avformat
    avcodec
    avutil
    swscale
    swresample
    SDL2
)

