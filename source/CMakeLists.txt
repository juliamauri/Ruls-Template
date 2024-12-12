find_package(SDL2 CONFIG REQUIRED)
find_package(imgui CONFIG REQUIRED)

add_executable (${TARGET_NAME})
target_sources(${TARGET_NAME} PRIVATE
    main.cpp
    JR_Application.cpp
    JR_Input.cpp
    JR_Window.cpp
    JR_WindowAndRenderer.cpp
    JR_WindowsManager.cpp
)
target_compile_definitions(${TARGET_NAME} PRIVATE IMGUI_DEFINE_MATH_OPERATORS)

target_link_libraries(${TARGET_NAME}
    PRIVATE
    $<TARGET_NAME_IF_EXISTS:SDL2::SDL2main>
    $<IF:$<TARGET_EXISTS:SDL2::SDL2>,SDL2::SDL2,SDL2::SDL2-static>
)
target_link_libraries(${TARGET_NAME} PRIVATE imgui::imgui)