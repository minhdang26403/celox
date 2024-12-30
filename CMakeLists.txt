cmake_minimum_required(VERSION 3.28)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON) # For clang-tidy and clangd.
set(CMAKE_C_STANDARD 17)
set(CMAKE_C_STANDARD_REQUIRED ON)

project(CraftingInterpreter VERSION 2024.1
  DESCRIPTION "A bytecode virtual machine"
  LANGUAGES C CXX)

# #####################################################################################################################
# COMPILER SETUP
# #####################################################################################################################

# Expected directory structure.
set(CELOX_BUILD_SUPPORT_DIR "${CMAKE_SOURCE_DIR}/build_support")
set(CELOX_CLANG_SEARCH_PATH "/usr/bin/" "/opt/homebrew/opt/llvm/bin/")

message(STATUS "You're using ${CMAKE_C_COMPILER_ID} ${CMAKE_C_COMPILER_VERSION}")

# Output directory
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

if(NOT DEFINED SANITIZER)
  set(SANITIZER thread)
endif()

set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS_DEBUG} -Wall -Wextra -Werror -Wno-unused-parameter")
set(CMAKE_C_FLAGS_DEBUG "${CMAKE_C_FLAGS_DEBUG} -O0 -g -fsanitize=${SANITIZER} -fno-omit-frame-pointer -fno-optimize-sibling-calls")

# #####################################################################################################################
# DEPENDENCIES
# #####################################################################################################################

# GoogleTest
include(FetchContent)
FetchContent_Declare(
  googletest
  URL https://github.com/google/googletest/archive/f8d7d77.zip
)
FetchContent_MakeAvailable(googletest)

enable_testing()
include(GoogleTest)

include_directories(${PROJECT_SOURCE_DIR}/src/include)

add_subdirectory(src)
add_subdirectory(test)
