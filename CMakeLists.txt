cmake_minimum_required(VERSION 3.20)

project(sdl2_vnc)

find_package(SDL2 CONFIG REQUIRED)

add_executable(sdl2_vnc
    SDL2_vnc.c SDL2_vnc.h
    vncc.c)

target_link_libraries(sdl2_vnc
    PRIVATE
    $<TARGET_NAME_IF_EXISTS:SDL2::SDL2main>
    $<IF:$<TARGET_EXISTS:SDL2::SDL2>,SDL2::SDL2,SDL2::SDL2-static>
)
