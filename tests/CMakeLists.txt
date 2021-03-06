# CMakeLists for Limba Unit Tests

link_libraries(${GLIB_LIBRARIES}
		${GLIB_GIO_LIBRARIES}
		${GLIB_GOBJECT_LIBRARIES}
		${APPSTREAM_LIBRARIES}
		limba
)

include_directories(${CMAKE_BINARY_DIR}
		${CMAKE_SOURCE_DIR}/src
		${CMAKE_CURRENT_SOURCE_DIR}
		${GLIB_INCLUDE_DIRS}
		${APPSTREAM_INCLUDE_DIRS}
)

# Basic tests
add_executable(li-test-basics test-basics.c)
add_dependencies(li-test-basics limba)
add_test(basic-test li-test-basics ${CMAKE_CURRENT_SOURCE_DIR})

# IPK package tests
add_executable(li-test-package test-package.c)
add_dependencies(li-test-package limba)
add_test(package-test li-test-package ${CMAKE_CURRENT_SOURCE_DIR})
set_property(TEST package-test APPEND PROPERTY DEPENDS basic-test)

# Software installation and management tests
add_executable(li-test-manager test-manager.c)
add_dependencies(li-test-manager limba)
add_test(manager-test li-test-manager ${CMAKE_CURRENT_SOURCE_DIR})
set_property(TEST manager-test APPEND PROPERTY DEPENDS package-test)
