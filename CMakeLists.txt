cmake_minimum_required(VERSION 3.16)

# Set your project name here
set(PROJECT_NAME App-Template)

# # User defined includes
include(cmake/project-functions.cmake)

# Include pico-sdk base cmake file
include(external/pico-sdk/external/pico_sdk_import.cmake)

# set up proejct
project(${PROJECT_NAME} C CXX ASM)
set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)

# Initialize the pico-sdk
pico_sdk_init()

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







# cmake_minimum_required(VERSION 3.16)

# # Include pico-sdk base cmake file
# include(external/pico-sdk/external/pico_sdk_import.cmake)

# project(App-Template)

# # Initialize the pico-sdk
# pico_sdk_init()

# # User defined includes
# include(cmake/project-functions.cmake)

# # Log output
# add_compile_definitions()

# # Add apps
# add_subdirectory(${CMAKE_SOURCE_DIR}/apps/template)
# add_subdirectory(${CMAKE_SOURCE_DIR}/apps/blinky)

# # Add modules
# # add_subdirectory(${CMAKE_SOURCE_DIR}/external/etl ${CMAKE_CURRENT_BINARY_DIR}/external/etl EXCLUDE_FROM_ALL)
# add_subdirectory(${CMAKE_SOURCE_DIR}/src/SEGGER_RTT_V752a EXCLUDE_FROM_ALL)
# add_subdirectory(${CMAKE_SOURCE_DIR}/src/logger EXCLUDE_FROM_ALL)

# # Print build info
# message(STATUS "****************************************************")
# message(STATUS "***   CMAKE_PROJECT_NAME:   ${CMAKE_PROJECT_NAME}")
# message(STATUS "***   CMAKE_BUILD_TYPE:     ${CMAKE_BUILD_TYPE}")
# message(STATUS "***   CMAKE_GENERATOR:      ${CMAKE_GENERATOR}")
# message(STATUS "***   PICO_PLATFORM:        ${PICO_PLATFORM}")
# message(STATUS "****************************************************")
