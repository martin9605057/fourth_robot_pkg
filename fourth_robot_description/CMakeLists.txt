cmake_minimum_required(VERSION 2.8.3)
project(fourth_robot_description)
find_package(catkin REQUIRED)

catkin_package()

# Install
set(LAUNCH_DIRS launch launch/config)
set(MESH_DIRS meshes/DAE/base meshes/DAE/wheel meshes/DAE/sensors/front_lrf meshes/DAE/sensors/gim30 meshes/DAE/sensors/gps meshes/DAE/sensors/rear_lrf meshes/STL/base meshes/STL/sensors/front_lrf meshes/STL/sensors/gim30 meshes/STL/sensors/gps meshes/STL/sensors/rear_lrf)
set(URDF_DIRS robots urdf urdf/base urdf/wheel urdf/sensors/gim30 urdf/sensors/gps urdf/sensors/lrf)

foreach(dir ${LAUNCH_DIRS} ${MESH_DIRS} ${URDF_DIRS})
  install(DIRECTORY ${dir}/
    DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/${dir})
endforeach(dir)

# Test
if (CATKIN_ENABLE_TESTING)
  find_package(roslaunch REQUIRED)
  roslaunch_add_file_check(launch)
endif()
