add_executable(glsl2cpp "${PROJECT_SOURCE_DIR}/CMakeModules/glsl2cpp.cpp")

set_target_properties(glsl2cpp PROPERTIES CXX_STANDARD 11)

include(GLSLtoH)

file(GLOB glsl_shaders "*.glsl")

list(SORT glsl_shaders)

source_group("src\\backend\\glsl_shaders" FILES ${glsl_shaders})

convert_glsl_shaders_to_headers(
    SOURCES ${glsl_shaders}
    VARNAME  shader_files
    EXTENSION "hpp"
    OUTPUT_DIR "shader_headers"
    TARGETS glsl_shader_targets
    NAMESPACE "glsl"
    EOD "0"
    )
