cmake_minimum_required(VERSION 3.8)
project(test_package)

include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
conan_basic_setup()

add_executable(${PROJECT_NAME} test_package.cpp)
target_link_libraries(${PROJECT_NAME} ${CONAN_LIBS})
target_compile_features(${PROJECT_NAME} PRIVATE cxx_std_11)
