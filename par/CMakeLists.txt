cmake_minimum_required(VERSION 3.20 FATAL_ERROR)
project(vtk-isovolume-parallel)

set(CMAKE_CXX_STANDARD 14)

set(FETCHCONTENT_QUIET OFF)

include(FetchContent)

FetchContent_Declare(
  VTK
  GIT_REPOSITORY https://gitlab.kitware.com/vtk/vtk.git
  GIT_TAG 433c353c14bea038b21881d94644049c5e3fbd1b
  GIT_PROGRESS ON
  SOURCE_DIR VTK
)
FetchContent_MakeAvailable(VTK)

add_executable(parIsovolume main.cxx)
target_link_libraries(parIsovolume PUBLIC VTK::CommonCore VTK::IOXML VTK::FiltersGeneral)

# vtk_module_autoinit is needed
vtk_module_autoinit(
  TARGETS parIsovolume
  MODULES VTK::CommonCore VTK::IOXML VTK::FiltersGeneral
)
