cmake_minimum_required(VERSION 3.15)
project(Kaleidoscope)

set(CMAKE_CXX_STANDARD 17)

# LLVM 경로 설정
set(LLVM_DIR "/opt/homebrew/opt/llvm/lib/cmake/llvm")

find_package(LLVM REQUIRED CONFIG)

include_directories(${LLVM_INCLUDE_DIRS})
add_definitions(${LLVM_DEFINITIONS})

file(GLOB SOURCES "src/*.cpp")  # src 폴더 안 모든 .cpp 가져오기

add_executable(kaleidoscope ${SOURCES})

llvm_map_components_to_libnames(llvm_libs support core irreader)
target_link_libraries(kaleidoscope ${llvm_libs})
