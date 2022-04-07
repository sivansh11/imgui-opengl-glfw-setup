cmake_minimum_required(VERSION 3.15)
project(app)

file(GLOB PROJECT_FILES src/*.cpp)


include_directories(include)

add_definitions("-D DEBUG" "-g")

set(IMGUI_DIR external/imgui/imgui)
set(IMGUI_BACKENDS_DIR ${IMGUI_DIR}/backends)

 
add_subdirectory(external/glfw)
add_subdirectory(external/glad)
add_subdirectory(external/imgui)

add_executable(${PROJECT_NAME} ${PROJECT_FILES})

target_include_directories(${PROJECT_NAME}
    PUBLIC external/glfw/include
    PUBLIC external/glad/include
    PUBLIC ${IMGUI_DIR}
    PUBLIC ${IMGUI_BACKENDS_DIR}
)

# target_link_directories(${PROJECT_NAME}
#     PUBLIC external/glfw/src
#     PUBLIC external/glad/src
#     PUBLIC external/imgui
#     PUBLIC external/stb_image/src
# )

target_link_libraries(${PROJECT_NAME}
    glfw
    glad
    imgui
)
