#*****************************************************************************
#**
#**
#**  Version : $Header:$
#**
#**
#**  Purpose : CMake master build script for the 'azure_demo' project.
#**
#**
#**  See Also: https://learnxinyminutes.com/docs/cmake/
#**            for an introduction to the CMake language.
#**
#**            https://cmake.org/cmake/help/v3.13/
#**            for complete documentation of the CMake language.
#**
#**            https://semver.org/
#**            for more on semantic versioning.
#**
#*****************************************************************************
cmake_minimum_required(VERSION 3.15)
#*****************************************************************************
project(azure_storage_demo VERSION 1.0.0)
#*****************************************************************************

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
#*****************************************************************************
# Include modules:
include(GNUInstallDirs) # For standard library locations

list(APPEND CMAKE_MODULE_PATH "${CMAKE_CURRENT_SOURCE_DIR}/cmake-modules")
include(AzureVcpkg)
az_vcpkg_integrate()

#*****************************************************************************

find_package(azure-storage-blobs-cpp CONFIG REQUIRED)

add_executable(${PROJECT_NAME} azure_demo.cpp)
target_link_libraries(${PROJECT_NAME} PRIVATE Azure::azure-storage-blobs)

#*****************************************************************************
