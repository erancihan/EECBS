cmake_minimum_required (VERSION 2.6)
project(eecbs)

cmake_policy(SET CMP0074 NEW)
cmake_policy(SET CMP0011 NEW)

IF(NOT CMAKE_BUILD_TYPE)
    SET(CMAKE_BUILD_TYPE "RELEASE")
ENDIF()

set(BOOST_ROOT "D:/boost/1_73_0")
set(BOOST_INCLUDEDIR "D:/boost/1_73_0")
set(Boost_USE_STATIC_LIBS ON)

include_directories("inc")
file(GLOB SOURCES "src/*.cpp")

# Find Boost
find_package( Boost 1.73.0 REQUIRED COMPONENTS program_options system filesystem)
include_directories( ${Boost_INCLUDE_DIRS} )

add_executable(eecbs ${SOURCES})
target_link_libraries(eecbs ${Boost_LIBRARIES})
