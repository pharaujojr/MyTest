CMAKE_MINIMUM_REQUIRED( VERSION 2.8.9 )

PROJECT( enyo-doom )

SET( TARGET enyo-doom )
SET( ENYO_DOOM_SRCS
	./e_mainwindow.cpp
	./main.cpp
)

SET( ENYO_DOOM_HDRS
	./e_mainwindow.h
)

SET( ENYO_DOOM_UIS
	./e_mainwindow.ui
)

SET( ENYO_DOOM_RCS
	./enyo-doom.qrc
)
include_directories ( ${CMAKE_SOURCE_DIR} ${CMAKE_BINARY_DIR} ${CMAKE_CURRENT_BINARY_DIR} )
find_package ( Qt5Core REQUIRED )
find_package (Qt5Widgets REQUIRED )
add_definitions ( $(Qt5Core_DEFINITIONS) )
add_definitions ( $(Qt5Widgets_DEFINITIONS) )
qt5_wrap_ui ( UI_HEADERS ${ENYO_DOOM_UIS} )
qt5_wrap_cpp ( MOC_SOURCES ${ENYO_DOOM_HDRS} )
qt5_add_resources ( RC_SOURCES ${ENYO_DOOM_RCS} )
include_directories ( ${Qt5Core_INCLUDE_DIRS} ${Qt5Widgets_INCLUDE_DIRS} )
add_executable ( enyo-doom ${UI_HEADERS} ${ENYO_DOOM_SRCS} ${ENYO_DOOM_HDRS} ${MOC_SOURCES} ${RC_SOURCES} )
target_link_libraries ( enyo-doom ${Qt5Widgets_LIBRARIES} ${Qt5Core_LIBRARIES} )

INSTALL( TARGETS enyo-doom DESTINATION bin )
INSTALL( FILES ./Changelog ./COPYING DESTINATION share/enyo-doom )
INSTALL( FILES ./enyo-doom.desktop DESTINATION share/applications )
INSTALL( FILES ./share/enyo_icon.png DESTINATION share/icons )
