cmake_minimum_required(VERSION 3.13...3.27)

set(PROJECT_NAME App-Template)

# initialize pico-sdk from submodule
# note: this must happen before project()
include(external/pico-sdk/pico_sdk_init.cmake)

# Include pico-sdk base cmake file
include(external/pico-sdk/external/pico_sdk_import.cmake)

# set(picotool_INSTALL_DIR external/picotool)
# set(PICOTOOL_FETCH_FROM_GIT_PATH external)
# set(picotool_DIR ${CMAKE_SOURCE_DIR}/external)

project(${PROJECT_NAME} C CXX ASM)
set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)

# initialize the Raspberry Pi Pico SDK
pico_sdk_init()

# rest of your project

# User defined includes
include(cmake/project-functions.cmake)

if (${BUILD_TARGET})
  message(STATUS "Build target: RP2040")
  add_subdirectory(src)
elseif(BUILD_TEST)
  message(STATUS "Build target: Unittest")
  add_subdirectory(test)
else()
  message(STATUS "Unknown target chosen")
endif()

# Print build info
message(STATUS "****************************************************")
message(STATUS "***   CMAKE_PROJECT_NAME:   ${CMAKE_PROJECT_NAME}")
message(STATUS "***   CMAKE_BUILD_TYPE:     ${CMAKE_BUILD_TYPE}")
message(STATUS "***   CMAKE_GENERATOR:      ${CMAKE_GENERATOR}")
message(STATUS "***   PICO_PLATFORM:        ${PICO_PLATFORM}")
message(STATUS "****************************************************")

