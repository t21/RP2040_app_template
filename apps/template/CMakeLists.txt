set(APP_NAME "Template")

add_executable(${APP_NAME}
  main.cpp
)

set_source_files_properties(
  main.cpp
  PROPERTIES
    COMPILE_FLAGS -Wall
    COMPILE_FLAGS -Werror
    COMPILE_FLAGS -Wextra
    COMPILE_FLAGS -Wshadow
)

pico_enable_stdio_usb(${APP_NAME} 0)
pico_enable_stdio_uart(${APP_NAME} 1)

pico_add_extra_outputs(${APP_NAME})

target_include_directories(${APP_NAME}
  PUBLIC
    .
    ${CMAKE_CURRENT_SOURCE_DIR}
)

target_link_libraries(${APP_NAME}
  PRIVATE
    pico_stdlib
    logger
)
