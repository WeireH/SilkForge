cmake_minimum_required(VERSION 3.16)
project(SilkForge)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_C_STANDARD 17)

# dependências locais (GLAD)
include_directories(${PROJECT_SOURCE_DIR}/dependencies/include)

# Inclui GLFW do Homebrew
include_directories(/opt/homebrew/include)
link_directories(/opt/homebrew/lib)

# Fonte principal + GLAD
set(SOURCES 
    main.cpp
    dependencies/src/glad.c
)

add_executable(SilkForge ${SOURCES})

# Linkar GLFW e OpenGL
target_link_libraries(SilkForge 
    glfw
    "-framework Cocoa"
    "-framework OpenGL"
    "-framework IOKit"
    "-framework CoreVideo"
)

