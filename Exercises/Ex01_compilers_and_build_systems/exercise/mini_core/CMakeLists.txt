cmake_minimum_required(VERSION 2.8.3)
project(mini_core)

# this is used to find a directory containing the named file and to store the result inside the variable EIGEN3_INCLUDE_DIR
find_path(EIGEN3_INCLUDE_DIR signature_of_eigen3_matrix_library
  /usr/include/eigen3
  /usr/local/include/eigen3
)

# check if variable is populated previously
if(NOT EIGEN3_INCLUDE_DIR)
  message(FATAL_ERROR "Please point the environment variable EIGEN3_INCLUDE_DIR to the include directory of your Eigen3 installation!")
endif()

# invokes the routines to find a package called Eigen3
find_package(Eigen3 REQUIRED)

# specify additional locations of header files
include_directories(${EIGEN3_INCLUDE_DIR} src/)

# add project source code
add_subdirectory(src)

add_subdirectory(executables)

add_executable(tutto
  executables/many_object_in_stack_example.cpp
  src/utils/property_eigen.cpp
  src/utils/blob.cpp
  src/utils/id_context.cpp
  src/utils/serializer.cpp
  src/utils/property.cpp
  src/utils/property_identifiable.cpp
  src/utils/deserializer.cpp
  src/utils/property_container.cpp
  src/utils/property_container_manager.cpp
  src/utils/serializable.cpp
  src/utils/serialization_context.cpp
  src/utils/id_placeholder.cpp
  src/utils/identifiable.cpp
  src/utils/object_data.cpp
  src/messages/pose_message.cpp
  src/messages/base_sensor_message.cpp
  src/messages/odometry_message.cpp
)
