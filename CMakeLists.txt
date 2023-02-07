cmake_minimum_required(VERSION 3.5)
project(boost_sml_vendor)

find_package(ament_cmake REQUIRED)

set(SML_BUILD_BENCHMARKS OFF CACHE BOOL "Build benchmarks")
set(SML_BUILD_EXAMPLES   OFF CACHE BOOL "Build examples")
set(SML_BUILD_TESTS      OFF CACHE BOOL "Build tests")
set(SML_USE_EXCEPTIONS   ON  CACHE BOOL "Do not disable exceptions")


include(FetchContent)
FetchContent_Declare(
  SML
  GIT_REPOSITORY https://github.com/boost-ext/sml
  GIT_TAG v1.1.6
)
FetchContent_MakeAvailable(SML)

ament_export_include_directories(include)

ament_package()