project(llvm-cbe)
if (USE_SYSTEM_LLVM)
  cmake_minimum_required(VERSION 3.4.3)
  find_package(LLVM REQUIRED CONFIG)
  message(STATUS "Found LLVM ${LLVM_PACKAGE_VERSION}")
  message(STATUS "Using LLVMConfig.cmake in: ${LLVM_DIR}")
  include_directories(${LLVM_INCLUDE_DIRS})
  add_definitions(${LLVM_DEFINITIONS})

  list(APPEND CMAKE_MODULE_PATH "${LLVM_CMAKE_DIR}")
  include(AddLLVM)
endif()

add_subdirectory(lib)
add_subdirectory(tools)

if( LLVM_INCLUDE_TESTS )
  add_subdirectory(unittests)
endif()
