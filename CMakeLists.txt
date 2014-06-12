# http://ros.org/doc/groovy/api/catkin/html/user_guide/supposed.html
cmake_minimum_required(VERSION 2.8.3)
project(hector_laserscan_to_pointcloud)

# Load catkin and all dependencies required for this package
# TODO: remove all from COMPONENTS that are not catkin packages.
find_package(catkin REQUIRED COMPONENTS roscpp laser_geometry laser_filters tf)

# include_directories(include ${Boost_INCLUDE_DIR} ${catkin_INCLUDE_DIRS})
# CATKIN_MIGRATION: removed during catkin migration
# cmake_minimum_required(VERSION 2.4.6)

# CATKIN_MIGRATION: removed during catkin migration
# include($ENV{ROS_ROOT}/core/rosbuild/rosbuild.cmake)

# Set the build type.  Options are:
#  Coverage       : w/ debug symbols, w/o optimization, w/ code-coverage
#  Debug          : w/ debug symbols, w/o optimization
#  Release        : w/o debug symbols, w/ optimization
#  RelWithDebInfo : w/ debug symbols, w/ optimization
#  MinSizeRel     : w/o debug symbols, w/ optimization, stripped binaries
#set(ROS_BUILD_TYPE RelWithDebInfo)


# CATKIN_MIGRATION: removed during catkin migration
# rosbuild_init()

#set the default path for built executables to the "bin" directory
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)
#set the default path for built libraries to the "lib" directory
set(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/lib)

#common commands for building c++ executables and libraries
#add_library(${PROJECT_NAME} src/example.cpp)
#target_link_libraries(${PROJECT_NAME} another_library)
#
# CATKIN_MIGRATION: removed during catkin migration
# rosbuild_add_boost_directories()
#find_package(Boost REQUIRED COMPONENTS thread)
include_directories(${Boost_INCLUDE_DIRS} ${catkin_INCLUDE_DIRS})


add_executable(laserscan_to_pointcloud_node src/laserscan_to_pointcloud_node.cpp)
target_link_libraries(laserscan_to_pointcloud_node ${Boost_LIBRARIES} ${catkin_LIBRARIES} )
add_dependencies(laserscan_to_pointcloud_node ${catkin_EXPORTED_TARGETS})

#target_link_libraries(${PROJECT_NAME})
## Generate added messages and services with any dependencies listed here
#generate_messages(
#TODO DEPENDENCIES geometry_msgs std_msgs
#)
# TODO: fill in what other packages will need to use this package
## LIBRARIES: libraries you create in this project that dependent projects also need
## CATKIN_DEPENDS: catkin_packages dependent projects also need
## DEPENDS: system dependencies of this project that dependent projects also need
catkin_package(
    DEPENDS
    CATKIN-DEPENDS roscpp laser_geometry laser_filters tf
    INCLUDE_DIRS ${Boost_INCLUDE_DIRS} ${catkin_INCLUDE_DIRS}
    LIBRARIES ${Boost_LIBRARIES} ${catkin_LIBRARIES}
)
