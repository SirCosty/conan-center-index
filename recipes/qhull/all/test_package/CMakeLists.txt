cmake_minimum_required(VERSION 3.1)
project(test_package C)

include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
conan_basic_setup(TARGETS)

find_package(Qhull REQUIRED CONFIG)

if(QHULL_REENTRANT)
    add_executable(${PROJECT_NAME} test_package_r.c)
    if(TARGET Qhull::qhull_r)
        target_link_libraries(${PROJECT_NAME} Qhull::qhull_r)
    else()
        target_link_libraries(${PROJECT_NAME} Qhull::qhullstatic_r)
    endif()
else()
    add_executable(${PROJECT_NAME} test_package.c)
    if(TARGET Qhull::libqhull)
        target_link_libraries(${PROJECT_NAME} Qhull::libqhull)
    else()
        target_link_libraries(${PROJECT_NAME} Qhull::qhullstatic)
    endif()
endif()
