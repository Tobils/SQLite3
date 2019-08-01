cmake_minimum_required(VERSION 3.5 FATAL_ERROR)

# setting crosscompiler
set(CROSS_COMPILING_ROOT /usr/local/share/gcc-linaro-6.3.1-2017.05-x86_64_arm-linux-gnueabihf)
set(CMAKE_C_COMPILER /usr/local/share/gcc-linaro-6.3.1-2017.05-x86_64_arm-linux-gnueabihf/bin/arm-linux-gnueabihf-gcc)
set(CMAKE_CXX_COMPILER /usr/local/share/gcc-linaro-6.3.1-2017.05-x86_64_arm-linux-gnueabihf/bin/arm-linux-gnueabihf-g++)

# setting untuk folder cmake
set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_CURRENT_SOURCE_DIR}/cmake")

# setting untuk source code
set(SOURCE_FILE
	src/main.cpp
)

# setting untuk output path dari file xecutable
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)

# setting untuk file executable nya
add_executable(db-tutorial ${SOURCE_FILE})

# cari package yang dibutuhkan
find_package (SQLite3)

if (SQLITE3_FOUND)
  include_directories(${SQLITE_INCLUDE_DIRS})
  target_link_libraries (db-tutorial ${SQLITE3_LIBRARIES})
endif (SQLITE3_FOUND)



