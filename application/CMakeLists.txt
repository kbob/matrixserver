project(application)

find_package(Boost 1.58.0 REQUIRED COMPONENTS thread log system)
include_directories(${Boost_INCLUDE_DIRS})

find_package(Eigen3 REQUIRED)
include_directories(${EIGEN3_INCLUDE_DIRS})

set(CMAKE_CXX_FLAGS "-fPIC")

set(SOURCE_FILES
        CubeApplication.cpp
        MatrixApplication.cpp Joystick.cpp Joystick.h)


add_library(application SHARED ${SOURCE_FILES})
target_link_libraries(application common)
target_link_libraries(application ${Boost_LIBRARIES} rt)
target_include_directories(application PUBLIC ${CMAKE_CURRENT_SOURCE_DIR} ${EIGEN3_INCLUDE_DIRS})

target_compile_definitions(application PUBLIC BOOST_LOG_DYN_LINK)