cmake_minimum_required(VERSION 3.10)
project(MyTestProject)

# 设置 C++ 标准
set(CMAKE_CXX_STANDARD 17)

# 查找必要的库
find_package(Boost REQUIRED)
find_package(GTest REQUIRED)
find_package(gflags REQUIRED)
find_package(glog REQUIRED)

# 添加可执行文件，假设你的主文件是 main.cpp
add_executable(my_test ./src/experimental/boost_function_test.cc)

# 链接库
target_link_libraries(my_test 
    PRIVATE 
    Boost::boost
    GTest::gtest 
    GTest::gtest_main
    gflags
    glog::glog
)

# 启用测试
include(GoogleTest)
gtest_discover_tests(my_test)