cmake_minimum_required(VERSION 3.10)
project(ignition_cmake2_vendor)

find_package(ament_cmake_core REQUIRED)
find_package(ament_cmake_vendor_package REQUIRED)

find_package(ignition-cmake2 2.6.2 QUIET)

ament_vendor(ignition_cmake2_vendor
  SATISFIED ${ignition-cmake2_FOUND}
  VCS_URL https://github.com/ignitionrobotics/ign-cmake.git
  VCS_VERSION ignition-cmake2_2.14.0
  CMAKE_ARGS
    -DBUILD_DOCS:BOOL=OFF
  GLOBAL_HOOK
)

find_package(ament_cmake_test REQUIRED)
if(BUILD_TESTING)
  find_package(ament_cmake_lint_cmake REQUIRED)
  find_package(ament_cmake_copyright REQUIRED)
  find_package(ament_cmake_xmllint REQUIRED)

  ament_lint_cmake()
  ament_copyright()
  ament_xmllint()
endif()

ament_package()
