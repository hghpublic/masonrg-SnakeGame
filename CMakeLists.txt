cmake_minimum_required(VERSION 3.30)

project(SnakeGame LANGUAGES CXX)

set(target ${PROJECT_NAME})
add_executable(${target})
target_compile_features(${target} PRIVATE cxx_std_26)

find_package(EnTT CONFIG REQUIRED)
target_link_libraries(${target} PRIVATE EnTT::EnTT)
find_package(SDL2 CONFIG REQUIRED)
target_link_libraries(${target} PRIVATE SDL2::SDL2)
find_package(SDL2_image CONFIG REQUIRED)
target_link_libraries(${target} PRIVATE SDL2_image::SDL2_image)
find_package(SDL2_ttf CONFIG REQUIRED)
target_link_libraries(${target} PRIVATE SDL2_ttf::SDL2_ttf)

add_subdirectory(Src)

# copy Assets

add_custom_command(TARGET ${target} POST_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy_directory 
        ${CMAKE_CURRENT_SOURCE_DIR}/Assets
        $<TARGET_FILE_DIR:${target}>/Assets)