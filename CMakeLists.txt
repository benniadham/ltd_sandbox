cmake_minimum_required(VERSION 3.10)

project (sandbox)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# configure 'liblib0.a' target
add_library( lib0-lib libs/lib0/lib0.cpp )
target_include_directories( lib0-lib PUBLIC "${PROJECT_BINARY_DIR}" )
target_include_directories( lib0-lib PUBLIC "${PROJECT_SOURCE_DIR}/inc/" )
set_target_properties( lib0-lib PROPERTIES OUTPUT_NAME lib0 )


# configure 'liblib1.a' target
add_library( lib1-lib libs/lib1/lib1.cpp )
target_include_directories( lib1-lib PUBLIC "${PROJECT_BINARY_DIR}" )
target_include_directories( lib1-lib PUBLIC "${PROJECT_SOURCE_DIR}/inc/" )
set_target_properties( lib1-lib PROPERTIES OUTPUT_NAME lib1 )


# configure 'hello' executable target
add_executable( hello-exe apps/hello/hello.cpp )
target_include_directories( hello-exe PUBLIC "${PROJECT_BINARY_DIR}")
target_include_directories( hello-exe PUBLIC "${PROJECT_SOURCE_DIR}/inc/")
set_target_properties( hello-exe PROPERTIES OUTPUT_NAME hello )
target_link_libraries( hello-exe lib0-lib lib1-lib  stdc++fs)


# configure 'demo' executable target
add_executable( demo-exe apps/demo/demo.cpp )
target_include_directories( demo-exe PUBLIC "${PROJECT_BINARY_DIR}")
target_include_directories( demo-exe PUBLIC "${PROJECT_SOURCE_DIR}/inc/")
set_target_properties( demo-exe PROPERTIES OUTPUT_NAME demo )
target_link_libraries( demo-exe lib0-lib lib1-lib  stdc++fs)


