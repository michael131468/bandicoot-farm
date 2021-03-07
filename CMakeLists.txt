cmake_minimum_required(VERSION 3.15)
project(BandicootFarm)

find_package(PkgConfig REQUIRED)
pkg_check_modules(BANDICOOT REQUIRED bandicoot)

add_executable(bandicoot_farm main.cpp)
target_include_directories(bandicoot_farm PUBLIC ${BANDICOOT_INCLUDE_DIRS})
target_link_libraries(bandicoot_farm LINK_PUBLIC ${BANDICOOT_LIBRARIES})

include(GNUInstallDirs)
install(TARGETS bandicoot_farm
	RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR}
	LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
	PUBLIC_HEADER DESTINATION ${CMAKE_INSTALL_INCLUDEDIR})
