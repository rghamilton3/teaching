cmake_minimum_required(VERSION 2.8 FATAL_ERROR)

project(PCL_Demo)

# configure PCL
find_package(PCL 1.7.1 REQUIRED)
include_directories(${PCL_INCLUDE_DIRS})
link_directories(${PCL_LIBRARY_DIRS})
add_definitions(${PCL_DEFINITIONS})

# configure OpenCV
find_package (OpenCV REQUIRED)

# suppress deprecation warnings
#set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wno-deprecated-declarations")

add_executable (openni2_snapper openni2_snapper.cpp)
target_link_libraries (openni2_snapper ${PCL_LIBRARIES})

add_executable (load_pcd load_pcd.cpp CloudVisualizer.cpp Utility.cpp)
target_link_libraries (load_pcd ${PCL_LIBRARIES} ${OpenCV_LIBS})
