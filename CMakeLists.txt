cmake_minimum_required(VERSION 2.8)

project(FS NONE)
include(UseLATEX)

add_custom_target(
    writegitid ALL
    COMMAND ${CMAKE_CURRENT_SOURCE_DIR}/write-gitid.sh
    WORKING_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}
)

set(DRAWINGS
    drawings/memory_hierachy.tex
    drawings/cache.tex
)

add_latex_document(
    formelsammlung.tex
    FORCE_PDF
    IMAGE_DIRS img
    INPUTS ${DRAWINGS}
    DEPENDS writegitid
)
