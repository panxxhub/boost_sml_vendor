cmake_minimum_required(VERSION 3.5)
project(boost_sml_vendor)


find_package(ament_cmake REQUIRED)

include(ExternalProject)

ExternalProject_Add(boost_sml
  PREFIX boost_sml
  URL https://github.com/boost-ext/sml/archive/refs/tags/v1.1.6.tar.gz
  URL_HASH MD5=b0432dce0645637881da5848791fdf18
  CMAKE_ARGS
   -DSML_BUILD_BENCHMARKS=OFF
   -DSML_BUILD_EXAMPLES=OFF
   -DSML_BUILD_TESTS=OFF
   -DSML_USE_EXCEPTIONS=ON
   -DCMAKE_INSTALL_PREFIX=${CMAKE_CURRENT_BINARY_DIR}/boost_sml_install
  INSTALL_DIR "${CMAKE_CURRENT_BINARY_DIR}/boost_sml_install"
)
install (DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}/boost_sml_install DESTINATION ${CMAKE_INSTALL_PREFIX})

   
install(DIRECTORY cmake DESTINATION share/${PROJECT_NAME})

ament_package()