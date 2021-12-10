# For more information about using CMake with Android Studio, read the
# documentation: https://d.android.com/studio/projects/add-native-code.html

# Sets the minimum version of CMake required to build the native library.

cmake_minimum_required(VERSION 3.10.2)

# Declares and names the project.

project("testnative")

# Creates and names a library, sets it as either STATIC
# or SHARED, and provides the relative paths to its source code.
# You can define multiple libraries, and CMake builds them for you.
# Gradle automatically packages shared libraries with your APK.
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include)
#include_directories(${CMAKE_CURRENT_SOURCE_DIR}/libutils/include)
#
#
#include_directories(${CMAKE_CURRENT_SOURCE_DIR}/native/include)
#include_directories(${CMAKE_CURRENT_SOURCE_DIR}/native/opengl/include)
#include_directories(include)
#include_directories(${CMAKE_CURRENT_SOURCE_DIR}/native/libs/nativewindow/include)
#include_directories(${CMAKE_CURRENT_SOURCE_DIR}/native/libs/nativedisplay/include)
#include_directories(${CMAKE_CURRENT_SOURCE_DIR}/native/libs/ui/include)
##native/libs/ui/include/ui/DisplayStatInfo.h
#include_directories(${CMAKE_CURRENT_SOURCE_DIR}/native/libs/binder/include)
#
#include_directories(${CMAKE_CURRENT_SOURCE_DIR}/native/services/surfaceflinger)
#include_directories(${CMAKE_CURRENT_SOURCE_DIR}/libcutils/include_vndk)
#include_directories(${CMAKE_CURRENT_SOURCE_DIR}/libcutils/include)
#
#
#
#
#
#include_directories(${CMAKE_CURRENT_SOURCE_DIR}/base/include)
#
#include_directories(${CMAKE_CURRENT_SOURCE_DIR}/bionic/libc/include)
#bionic/bionic/libc/include/sys/system_properties.h


#libcutils/include/cutils/trace.h


#native/libs/ui/include/ui/DisplayStatInfo.h

file(GLOB_RECURSE nativeSrc  *.cpp *.c )
add_library( # Sets the name of the library.
             native-lib

             # Sets the library as a shared library.
             SHARED

             # Provides a relative path to your source file(s).
             native-lib.cpp
            ${nativeSrc}
        )

# Searches for a specified prebuilt library and stores the path as a
# variable. Because CMake includes system libraries in the search path by
# default, you only need to specify the name of the public NDK library
# you want to add. CMake verifies that the library exists before
# completing its build.

find_library( # Sets the name of the path variable.
              log-lib

              # Specifies the name of the NDK library that
              # you want CMake to locate.
              log )

# Specifies libraries CMake should link to your target library. You
# can link multiple libraries, such as libraries you define in this
# build script, prebuilt third-party libraries, or system libraries.

target_link_libraries( # Specifies the target library.
                       native-lib

                       # Links the target library to the log library
                       # included in the NDK.
                       ${log-lib} )