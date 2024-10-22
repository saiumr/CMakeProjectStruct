project(example)

set(example_dirs
    audio
    core
    models
    )

set(example_sources)
set(example_resources)

foreach (example_dir ${example_dirs})
    file(GLOB sources ${example_dir}/*.cpp)
    list(APPEND example_sources ${sources})

    file(GLOB resources ${example_dir}/resources/*)
    list(APPEND example_resources ${resources})
endforeach ()

foreach (example_source ${example_sources})
    get_filename_component(example_name ${example_source} NAME)
    string(REPLACE ".cpp" "" example_name ${example_name})

    add_executable(${example_name} ${example_source})

    string(REGEX MATCH ".*/.*/" resources_dir ${example_source})
    string(APPEND resources_dir "resources")
endforeach ()

file(COPY ${example_resources} DESTINATION "resources/")

