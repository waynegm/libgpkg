# Compile Instructions
## Supported Platforms
- Microsoft Windows XP or higher (x86 and x64)
- Linux (x86 and x64) (tested mainly on Ubuntu and ArchLinux)
- Mac OS X 10.5 or higher (x86 and x64)
- Android

## Supported Compilers
libgpkg is mostly written in ISO C99. It should therefor be compilable with most standards compliant compilers. Compiler specific intrinsics and attributes are used for thread local storage and atomic operations on certain platforms. The project is tested with the following compilers:

- GNU Compiler Collection
- LLVM CLang
- Microsoft Visual C++

Note that compilation with Microsoft Visual C++ requires that the compiler is set to C++ mode (/Tp or /TP) to work around the lack of C99 support in this compiler.

## Dependencies
The base libgpkg library has the following external dependencies:

- C99 standard library
- SQLite 3.7 or higher

When geometry functions are enabled at compile time, the following additional dependencies are required:

    GEOS 3.2 or higher
    POSIX threads (on Unix-like platforms with compilers that do not support the __thread storage class)

## Instructions for Windows, Linux and Mac OS X
The following build tools are required in order to compile the library:

    CMake 2.7 or higher (for Linux, Mac OS X and Windows)
    A supported compiler toolchain

Open a terminal (or command prompt) and change to the root directory of the project. Create an output directory in the project directory ('build' is used in these instructions) and change to this directory.

mkdir build
cd build

Generate the appropriate build scripts for your platform using cmake. On Linux and Mac OS X you should use the 'Unix Makefiles' generator. On Windows use the 'NMake Makefiles' generator.

cmake -G 'Unix Makefiles' ..

or

cmake -G 'NMake Makefiles' ..

Build the project using the generated build scripts.

make

or

nmake

If the compilation completed without errors you should now find libgpkg.so (or gpkg.dll) under build/gpkg and gpkg (or gpkg.exe) under build/shell. libgpkg.so is the SQLite loadable extension. gpkg is an extended version of the SQLite command line shell that preloads libgpkg in auto mode.

## CMake Options
The CMake scripts support the following options that control library compilation

    GPKG_GEOS:BOOL (default: OFF)

    Determines if GEOS is enabled or not. This option should be enabled to include geometry functions in libgpkg

    GPKG_TEST:BOOL (default: OFF)

    Determines if unit tests should be enabled or not. Execution of the unit tests requires a Ruby 1.9 or higher interpreter. Unit tests can be executed by running the test target.

    GPKG_COVERAGE:BOOL (default: OFF)

    Determines if code coverage information should be generated or not when running the unit tests. This option currently requires compilation using GCC and the gcov code coverage tool.

## Instructions for Android
Compiling for Android requires the Android NDK. An Android.mk is included that can be used to compile the libgpkg.so SQLite loadable extension.

