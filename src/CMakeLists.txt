# Define the library
add_library(lox
  chunk.c
  debug.c
  memory.c
  value.c
)

# Define the executable
add_executable(celox main.c)

# Link the executable with the lox library
target_link_libraries(celox PRIVATE lox)