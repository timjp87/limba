# CMakeLists for UAI Unit Tests

link_libraries(${GLIB_LIBRARIES}
		${GLIB_GIO_LIBRARIES}
		${GLIB_GOBJECT_LIBRARIES}
		listaller
)

include_directories(${CMAKE_BINARY_DIR}
		${CMAKE_SOURCE_DIR}/src
		${CMAKE_CURRENT_SOURCE_DIR}
		${GLIB_INCLUDE_DIRS}
)

# Basic tests
add_executable(li-test-basics test-basics.c)
add_dependencies(li-test-basics listaller)
add_test(basic-test li-test-basics ${CMAKE_CURRENT_SOURCE_DIR})