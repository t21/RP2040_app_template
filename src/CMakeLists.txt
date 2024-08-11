# Set your project sources here
set(PROJECT_SOURCES
  main.cpp
)

# # Initialize the pico-sdk
# pico_sdk_init()

add_executable(${PROJECT_NAME}
  ${PROJECT_SOURCES}
)

set_source_files_properties(
  ${PROJECT_NAME}
  PROPERTIES
  COMPILE_FLAGS -Wall
  COMPILE_FLAGS -Werror
  COMPILE_FLAGS -Wextra
  COMPILE_FLAGS -Wshadow
  COMPILE_FLAGS -Wpedantic
)

# Add modules
add_subdirectory(${CMAKE_SOURCE_DIR}/src/SEGGER_RTT_V752a EXCLUDE_FROM_ALL)
add_subdirectory(${CMAKE_SOURCE_DIR}/src/logger EXCLUDE_FROM_ALL)

# pico_enable_stdio_usb(${APP_NAME} 0)
# pico_enable_stdio_uart(${APP_NAME} 0)

pico_add_extra_outputs(${PROJECT_NAME})

# target_include_directories(${APP_NAME}
#   PUBLIC
#     ${CMAKE_CURRENT_SOURCE_DIR}
# )

target_link_libraries(${PROJECT_NAME}
  PRIVATE
  pico_stdlib
  logger
)


# ------------



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
