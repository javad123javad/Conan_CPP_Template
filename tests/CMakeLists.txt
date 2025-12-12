include(GoogleTest)
find_package(GTest REQUIRED)

add_executable(test_template test_template.cpp)
target_link_libraries(test_template PRIVATE GTest::gtest GTest::gtest_main)

target_include_directories(test_template PRIVATE ${CMAKE_SOURCE_DIR})
target_include_directories(test_template PRIVATE ${CMAKE_SOURCE_DIR}/src)
gtest_discover_tests(test_template)
