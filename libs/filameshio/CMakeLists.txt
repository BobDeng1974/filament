cmake_minimum_required(VERSION 3.1)
project(filameshio)

set(TARGET filameshio)
set(PUBLIC_HDR_DIR include)

# ==================================================================================================
# Sources and headers
# ==================================================================================================
set(PUBLIC_HDRS ${PUBLIC_HDR_DIR}/${TARGET}/MeshIO.h)
set(DIST_HDRS ${PUBLIC_HDR_DIR}/${TARGET}/MeshIO.h)
set(SRCS src/MeshIO.cpp)

# ==================================================================================================
# Includes and target definition
# ==================================================================================================
include_directories(${PUBLIC_HDR_DIR})
add_library(${TARGET} STATIC ${PUBLIC_HDRS} ${SRCS})
target_include_directories(${TARGET} PUBLIC ${PUBLIC_HDR_DIR})
target_link_libraries(${TARGET} PUBLIC filament)

# ==================================================================================================
# Installation
# ==================================================================================================
set(INSTALL_TYPE ARCHIVE)
install(TARGETS ${TARGET} ${INSTALL_TYPE} DESTINATION lib/${DIST_DIR})
install(FILES ${DIST_HDRS} DESTINATION include/${TARGET})
