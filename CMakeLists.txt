project(stub-cpp-sfml)
cmake_minimum_required(VERSION 2.8)

# enable C++11 features for gcc and clang
if(CMAKE_COMPILER_IS_GNUCXX)
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++0x")
elseif(CMAKE_CXX_COMPILER_ID STREQUAL "Clang")
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++0x")

    # use libc++ in Mac OS X
    if(${CMAKE_SYSTEM_NAME} MATCHES Darwin)
        set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -stdlib=libc++")
    endif()
endif()

# use FindSFML.cmake to load SFML support
set(CMAKE_MODULE_PATH "${CMAKE_MODULE_PATH};${CMAKE_CURRENT_SOURCE_DIR}/CMake")
find_package(SFML 2 COMPONENTS audio graphics window system network REQUIRED)
include_directories(${SFML_INCLUDE_DIR})

# game executable
set(GAME ${PROJECT_NAME})
set(HEADERS )
set(SOURCES )
add_executable(${GAME} ${HEADERS} ${SOURCES})
target_link_libraries(${GAME} ${SFML_LIBRARIES})

# installation
# TODO
