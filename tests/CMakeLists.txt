include(CTest)

set(TARGET_NAME run_tests)

# Executable
add_executable(${TARGET_NAME} run_tests.cpp)
target_sources(${TARGET_NAME} PRIVATE
        linked_list_tests.cpp
        linked_queue_tests.cpp
        array_stack_tests.cpp
        dynamic_array_tests.cpp)

# Catch2
target_link_libraries(${TARGET_NAME} PRIVATE ${PROJECT_NAME} Catch2::Catch2)

# Discover tests
include(${PROJECT_SOURCE_DIR}/contrib/Catch2/contrib/Catch.cmake)
catch_discover_tests(${TARGET_NAME} EXTRA_ARGS -r console --abort)
