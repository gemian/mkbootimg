cmake_minimum_required(VERSION 3.7)
project(mkbootimg)
string(TOLOWER ${PROJECT_NAME} PROJECT_NAME_LOWER)

set(CMAKE_CXX_STANDARD 14)

include(GNUInstallDirs)
find_package(PkgConfig REQUIRED)

set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -g -pthread -std=c11 -Werror -Wall -Wextra -pedantic")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -g -pthread -std=c++14 -Werror -Wall -Wnon-virtual-dtor -Wextra -pedantic")

include_directories(
		${CMAKE_CURRENT_BINARY_DIR}
)

add_subdirectory(mincrypt)

add_executable(${PROJECT_NAME_LOWER}
		mkbootimg.c
		)

target_link_libraries(${PROJECT_NAME_LOWER}
		libmincrypt
		)

add_executable(unpackbootimg
		unpackbootimg.c
		)

install(TARGETS ${PROJECT_NAME_LOWER} RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR})
install(TARGETS unpackbootimg RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR})
