CMakeLists.txt Demo:
cmake_minimum_required (VERSION 2.6)
project (BenchmarkTool)
 
# Add the header
include_directories(include)
include_directories(/home/v-xianly/projects/NNPACK/include)
include_directories(/home/v-xianly/projects/NNPACK/deps/pthreadpool/include)

# Add the source
aux_source_directory(./src DIR_SRCS)

# Add the libraries
link_directories("/home/v-xianly/projects/NNPACK/lib/")

# Add the executable
add_executable(BenchmarkTool ${DIR_SRCS})
target_link_libraries (BenchmarkTool libnnpack.a libcpuinfo.a libpthreadpool.a libpthread.so)