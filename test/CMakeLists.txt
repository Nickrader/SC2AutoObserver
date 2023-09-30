include_directories(${PROJECT_SOURCE_DIR})
include_directories(${PROJECT_SOURCE_DIR}/build/_deps/googletest-src/googlemock/include)

add_executable(
    TestArgParser
    ${PROJECT_SOURCE_DIR}/src/ArgParser.h
    ${PROJECT_SOURCE_DIR}/src/ArgParser.cpp
    ArgParser.test.cpp)

target_link_libraries(TestArgParser GTest::gtest_main)
