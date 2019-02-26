cmake_minimum_required(VERSION 2.8)

project(EER NONE)
include(UseLATEX)

file(COPY ${CMAKE_CURRENT_SOURCE_DIR}/mTex 
    DESTINATION ${CMAKE_CURRENT_BINARY_DIR}
)

add_custom_target(
    writegitid ALL
    COMMAND ${CMAKE_CURRENT_SOURCE_DIR}/write-gitid.sh
    WORKING_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}
)

add_latex_document(
    ERR.tex
    FORCE_PDF
    IMAGE_DIRS img
    DEPENDS writegitid
)

add_latex_document(
    Einfuehrung_Roboterregelung.tex
    FORCE_PDF
    IMAGE_DIRS img
    DEPENDS writegitid
)
