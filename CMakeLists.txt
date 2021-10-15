cmake_minimum_required (VERSION 2.6)
project(eecbs)

cmake_policy(SET CMP0074 NEW)
cmake_policy(SET CMP0011 NEW)

IF(NOT CMAKE_BUILD_TYPE)
    SET(CMAKE_BUILD_TYPE "RELEASE")
ENDIF()


IF(NOT DEFINED NO_WAIT)
    set(NO_WAIT 0)
ENDIF()
IF(NOT DEFINED DISAPPEAR_AT_TARGET)
    set(DISAPPEAR_AT_TARGET 0)
ENDIF()


IF(NO_WAIT)
    MESSAGE("Building WITHOUT Wait action")
    add_compile_definitions(NO_WAIT=1)
ELSE()
    MESSAGE("Building WITH Wait action")
    add_compile_definitions(NO_WAIT=0)
ENDIF()

IF(DISAPPEAR_AT_TARGET)
    MESSAGE("Building WITH DISAPPEAR AT TARGET")
    add_compile_definitions(DISAPPEAR_AT_TARGET=1)
ELSE()
    MESSAGE("Building WITHOUT DISAPPEAR AT TARGET")
    add_compile_definitions(DISAPPEAR_AT_TARGET=0)
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
