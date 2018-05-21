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




#Build lib
add_library (xxx "${SOURCES}")

#Build dll
add_library (xxx shared "${SOURCES}")

#Build dll + lib 
add_definitions(-DBUILD_LIBRARY)
add_library (xxx shared "${SOURCES}")
.h file:
#if defined(_MSC_VER)
# if defined(BUILD_LIBRARY)
#  define XXX_API __declspec(dllexport)
# else
#  define XXX_API __declspec(dllimport)
# endif
#elif defined(__GNUC__)
# if defined(BUILD_LIBRARY)
#  define XXX_API __attribute__((visibility("default")))
# else
#  define XXX_API
# endif
#else
# pragma warning Unknown dynamic link import/export semantics.
#endif

XXX_API void function(xxxx);