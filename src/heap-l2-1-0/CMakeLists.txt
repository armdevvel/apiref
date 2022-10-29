cmake_minimum_required(VERSION 3.5)
project(heap-l2-1-0 LANGUAGES C)

set(CMAKE_INCLUDE_CURRENT_DIR ON)

add_custom_target(${PROJECT_NAME} ALL
    ${CMAKE_C_COMPILER} -nodefaultlibs -nostdlib -shared -Wl,-non_shared -o "\"${PROJECT_BINARY_DIR}/api-ms-win-core-heap-l2-1-0.dll\"" "\"${apiref_SOURCE_DIR}/template-dll.c\"" "\"${PROJECT_SOURCE_DIR}/api-ms-win-core-heap-l2-1-0.def\"" -e DllMain
)

install(PROGRAMS ${PROJECT_BINARY_DIR}/api-ms-win-core-heap-l2-1-0.dll DESTINATION bin)