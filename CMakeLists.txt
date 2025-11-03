project(imgui)

file(GLOB IMGUI_SOURCES "./*.cpp")
file(GLOB IMGUI_HEADERS "src/*.h")

add_library(imgui STATIC ${IMGUI_SOURCES} ${IMGUI_HEADERS})

target_include_directories(imgui PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}/*.h
)

target_compile_features(imgui PUBLIC cxx_std_17)
# 设置库的输出名称
set_target_properties(imgui PROPERTIES
    OUTPUT_NAME "imgui"
)

# 安装配置
install(TARGETS imgui
    RUNTIME DESTINATION bin
    LIBRARY DESTINATION lib
    ARCHIVE DESTINATION lib
)

install(DIRECTORY ./ DESTINATION include/imgui FILES_MATCHING PATTERN "*.h")
