cmake_minimum_required(VERSION 3.30)
project(Stormllama)

set(CMAKE_CXX_STANDARD 20)

find_package(Threads REQUIRED)

include_directories(${CMAKE_SOURCE_DIR}/ixwebsocket)

add_executable(Stormllama main.cpp)

# Add precompiled headers
target_precompile_headers(Stormllama PRIVATE
        ${CMAKE_SOURCE_DIR}/pch.hpp
)

# Link libraries
target_link_libraries(Stormllama
        ${CMAKE_SOURCE_DIR}/libixwebsocket.a
        Threads::Threads
        -lz
        -lssl
        -lcrypto
)
