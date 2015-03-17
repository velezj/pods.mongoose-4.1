cmake_minimum_required(VERSION 2.6.0)

# pull in the pods macros. See cmake/pods.cmake for documentation
set(POD_NAME mongoose-4.1)
include(cmake/pods.cmake)

set(CMAKE_C_FLAGS_DEBUG "${CMAKE_C_FLAGS} -DENABLE_DBG")

add_library( mongoose-4.1 SHARED
  mongoose/mongoose.c
)
pods_install_headers(
  mongoose/mongoose.h
  DESTINATION
  mongoose
)
pods_use_pkg_config_packages(mongoose-4.1 boost-1.54.0)
pods_install_libraries( mongoose-4.1 )
pods_install_pkg_config_file(mongoose-4.1
    CFLAGS
    LIBS -lmongoose-4.1 -lpthread
    REQUIRES boost-1.54.0
    VERSION 4.1.0)

