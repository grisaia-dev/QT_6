cmake_minimum_required(VERSION 3.5)
project(PreGraphic VERSION 0.1 LANGUAGES CXX)

set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(EXECUTABLE_OUTPUT_PATH ${CMAKE_SOURCE_DIR}/bin/)

if(WIN32)
    set(CMAKE_PREFIX_PATH "C:/Qt/6.5.2/msvc2019_64")
endif()

find_package(QT NAMES Qt6 Qt5 REQUIRED COMPONENTS Widgets Concurrent Charts)
find_package(Qt${QT_VERSION_MAJOR} REQUIRED COMPONENTS Widgets Concurrent Charts)

set(PROJECT_HEADERS_FILES
        lib/mainwindow.h
)

set(PROJECT_SOURCES_FILES 
        main.cpp
        lib/mainwindow.cpp
        lib/mainwindow.ui
)

qt_add_executable(${PROJECT_NAME} MANUAL_FINALIZATION ${PROJECT_HEADERS_FILES} ${PROJECT_SOURCES_FILES})
target_link_libraries(${PROJECT_NAME} PRIVATE Qt${QT_VERSION_MAJOR}::Widgets Qt${QT_VERSION_MAJOR}::Concurrent Qt${QT_VERSION_MAJOR}::Charts)
#qt_finalize_executable(${PROJECT_NAME})