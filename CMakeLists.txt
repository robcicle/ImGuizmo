project(ImGuizmo)
add_library(ImGuizmo STATIC)

target_include_directories(ImGuizmo 
PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}
PRIVATE
    ${CMAKE_CURRENT_SOURCE_DIR}/../imgui
)

set(IMGUIZMO_SOURCES
    ImGuizmo.cpp
    ImGuizmo.h
)

target_sources(ImGuizmo PRIVATE ${IMGUIZMO_SOURCES})

target_compile_definitions(ImGuizmo PRIVATE 
    $<$<CONFIG:Debug>:IMGUIZMO_DEBUG>
    $<$<CONFIG:Release>:IMGUIZMO_RELEASE>
    $<$<CONFIG:Dist>:IMGUIZMO_DIST>
)

target_compile_options(ImGuizmo PRIVATE 
    $<$<CONFIG:Debug>:-g>
    $<$<CONFIG:Release>:-O2>
    $<$<CONFIG:Dist>:-O2 -s>
)
