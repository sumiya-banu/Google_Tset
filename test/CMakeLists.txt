set(This ExampleTest)

set(Sources 
    ExampleTest.cpp
)

add_executable(${This} ${Sources})
target_link_libraries(${This} gtest_main Example)

include(GoogleTest)
gtest_discover_tests(${This})
