cmake_minimum_required(VERSION 3.5)
project(processthreads-l1-1-0 LANGUAGES C)

set(CMAKE_INCLUDE_CURRENT_DIR ON)

add_custom_target(${PROJECT_NAME}-def ALL
    ${CMAKE_C_COMPILER} -nodefaultlibs -nostdlib -shared -Wl,-non_shared -o "\"api-ms-win-core-processthreads-l1-1-0.lib\"" "\"${PROJECT_SOURCE_DIR}/api-ms-win-core-processthreads-l1-1-0.def\""
)

add_custom_target(${PROJECT_NAME} ALL
    ${CMAKE_C_COMPILER} -nodefaultlibs -nostdlib -shared -Wl,-non_shared -o "\"${PROJECT_BINARY_DIR}/api-ms-win-core-processthreads-l1-1-0.dll\"" "\"${apiref_SOURCE_DIR}/template-dll.c\"" "\"${PROJECT_SOURCE_DIR}/api-ms-win-core-processthreads-l1-1-0.def\"" -e DllMain
)

install(PROGRAMS ${PROJECT_BINARY_DIR}/api-ms-win-core-processthreads-l1-1-0.lib DESTINATION lib)
install(PROGRAMS ${PROJECT_BINARY_DIR}/api-ms-win-core-processthreads-l1-1-0.dll DESTINATION bin)