# Define the library
add_library(lox
  chunk.c
  compiler.c
  debug.c
  memory.c
  object.c
  scanner.c
  table.c
  value.c
  vm.c
)

# Add an option for NAN_BOXING with a default value of OFF (0)
option(NAN_BOXING "Enable NaN Boxing for value representation" OFF)

# Add DEBUG_* flags for Debug builds only
target_compile_definitions(lox PRIVATE
  $<$<BOOL:${NAN_BOXING}>:NAN_BOXING> # Define NAN_BOXING only if enabled
  $<$<CONFIG:Debug>:
  DEBUG_TRACE_EXECUTION;
  DEBUG_PRINT_CODE;
  DEBUG_STRESS_GC;
  DEBUG_LOG_GC> # Define in Debug builds
)

# Define the executable
add_executable(celox main.c)

# Link the executable with the lox library
target_link_libraries(celox PRIVATE lox)
