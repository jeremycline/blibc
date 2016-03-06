cmake_minimum_required(VERSION 3.0.0)

project(blibc C)
set(CMAKE_SYSTEM_VERSION 1.0.0)

# Build the kernel and its dependencies
include_directories("libc/include")

# Configure the following C flags:
#
#   -g:             Include debugging information.
#   -std=gnu11:     Explicitly set the C standard to GNU 2011.
#   -nostdlib:      We *are* stdlib
#   -Wall:          Enable all warnings about constructions that some users consider questionable.
#   -Wextra:        Enable extra warnings not turned on by '-Wall'.
#   -Werror:        Force all warnings to be compilation errors.
set(CMAKE_C_FLAGS "-g -std=gnu11 -nostdlib -Wall -Wextra -Werror")

file(GLOB_RECURSE BLIBC_SOURCES "libc/*.c")

# Define the kernel image and its build requirements.
add_library(c SHARED ${BLIBC_SOURCES})

