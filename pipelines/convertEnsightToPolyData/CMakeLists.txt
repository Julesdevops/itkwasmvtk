cmake_minimum_required(VERSION 3.16)
project(convertEnsightToPolyData)

set(CMAKE_CXX_STANDARD 17)

# We always want to build against the WebAssemblyInterface module.
set(itk_components
  WebAssemblyInterface
)

find_package(VTK REQUIRED
  COMPONENTS IOExport IOXML IOLegacy FiltersGeometry FiltersGeneral IOEnSight
)

find_package(ITK REQUIRED 
  COMPONENTS ${itk_components}
)

include(${ITK_USE_FILE})

add_executable(convertEnsightToPolyData main.cxx)

target_link_libraries(convertEnsightToPolyData PUBLIC ${VTK_LIBRARIES} ${ITK_LIBRARIES} )
