project( laghos )
include(blt/SetupBLT.cmake)
include(cmake/SetupMFEM.cmake)

set(laghos_sources serial/laghos_assembly_s.cpp
                   serial/laghos_s.cpp
                   serial/laghos_solver_s.cpp)

set(laghos_headers serial/laghos_assembly_s.hpp
                   serial/laghos_solver_s.hpp)


set(laghos_sources_mpi laghos_assembly.cpp
                       laghos.cpp
                       laghos_solver.cpp)

set(laghos_headers_mpi laghos_assembly.hpp
                       laghos_solver.hpp)

blt_add_executable(
    NAME        laghos_ser
    HEADERS     ${laghos_headers}
    SOURCES     ${laghos_sources} 
    DEPENDS_ON  mfem)

blt_add_executable(
    NAME        laghos_mpi
    HEADERS     ${laghos_headers_mpi}
    SOURCES     ${laghos_sources_mpi} 
    DEPENDS_ON  mfem mpi)

