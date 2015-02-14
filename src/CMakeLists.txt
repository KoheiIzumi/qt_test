cmake_minimum_required(VERSION 2.6)
 
project(qt_test)
 
find_package(Qt4 REQUIRED)
 
set(qt_test_SOURCES
        main.cpp
        mainwindow.cpp
)
set(qt_test_FORMS
        mainwindow.ui
)
set(qt_test_RESOURCES
)
set(qt_test_HEADERS
        mainwindow.h
)
 
INCLUDE(${QT_USE_FILE})
 
QT4_WRAP_CPP(qt_test_HEADERS_MOC ${qt_test_HEADERS})
QT4_WRAP_UI(qt_test_FORMS_HEADERS ${qt_test_FORMS})
QT4_ADD_RESOURCES(qt_test_RESOURCES_RCC ${qt_test_RESOURCES})
 
include_directories(
	.
	${CMAKE_CURRENT_BINARY_DIR}
)

add_definitions(${QT_DEFINITIONS})
 
add_executable(qt_test 
	${qt_test_SOURCES}
        ${qt_test_HEADERS_MOC}
        ${qt_test_FORMS_HEADERS}
        ${qt_test_RESOURCES_RCC}
)

target_link_libraries(qt_test ${QT_LIBRARIES})
