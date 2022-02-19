# nicemake

This is a set of functions to make simple cmake targets a bit less annoying to write.

## Usage

As a first step, `include("build-utils.cmake")` from your `CMakeLists.txt`.

You may now add an executable binary target as follows:

```
nmk_binary(NAME your_target_name
           SRCS ${CMAKE_CURRENT_LIST_DIR}/source-file-1.cpp
                ${CMAKE_CURRENT_LIST_DIR}/header-file-1.h
                ${CMAKE_CURRENT_LIST_DIR}/source-file-2.cpp
           PVT_INCLUDES ${CMAKE_CURRENT_LIST_DIR}/include/path/for/your/target
           DEPS dependency1 dependency2 dependency3
           PVT_DEFINES YOUR_CUSTOM_PREPROCESSOR_DEFINITIONS_HERE
           OUTPUT_DIR ${CMAKE_CURRENT_LIST_DIR}/folder/to/put/the/executable/into)
```

You may add a static library target as follows:

```
nmk_static_library(NAME your_library_name
                   SRCS ${CMAKE_CURRENT_LIST_DIR}/source-file-1.cpp
                        ${CMAKE_CURRENT_LIST_DIR}/source-file-2.cpp
                   PVT_INCLUDES ${CMAKE_CURRENT_LIST_DIR}/path/to/your/library
                   PUB_INCLUDES ${CMAKE_CURRENT_LIST_DIR}/path/to/your/library/include # Shall be added to the include paths of all targets dependent on this target.
                   PUB_DEFINES  YOUR_CUSTOM_DEFINE_HERE # Shall be added to the preprocessor definitions of all targets dependent on this target.
                   DEPS dependency1 dependency2)
```

You may add a header-only library as follows:

```
nmk_header_library(NAME your_library_name
                   SRCS ${CMAKE_CURRENT_LIST_DIR}/path/to/lib/header-file-1.h
                        ${CMAKE_CURRENT_LIST_DIR}/path/to/lib/header-file-2.h
                   PUB_INCLUDES ${CMAKE_CURRENT_LIST_DIR}/path/to/lib)
```
