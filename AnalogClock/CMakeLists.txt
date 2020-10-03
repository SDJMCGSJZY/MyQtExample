cmake_minimum_required(VERSION 3.10)

# your project name
project(AnalogClock)

# find includes in the corresponding build directories
set(CMAKE_INCLUDE_CURRENT_DIR ON)
# run moc automatically
set(CMAKE_AUTOMOC ON)
# if you're using Widgets and editing .ui forms in Designer
set(CMAKE_AUTOUIC ON)

message("Looking for Qt...")
# Qt modules (https://doc.qt.io/qt-5/qtmodules.html) you're using in your application
find_package(Qt5 REQUIRED Widgets)
if (${Qt5_FOUND})
    message("Found Qt " ${Qt5_VERSION})
else()
    message("Couldn't find Qt")
endif()


FILE(GLOB_RECURSE CURRENT_INCLUDE *.h)
FILE(GLOB_RECURSE CURRENT_SOURCES *.CPP)
FILE(GLOB_RECURSE CURRENT_FORM *.ui)

# your source files
#set(sources
#    Mainwindow.ui
#    Mainwindow.cpp
#    main.cpp
#)
# name of the .exe file, window flag and the list of things to compile
#add_executable(${CMAKE_PROJECT_NAME} WIN32 ${sources})
#add_executable(Qt_cmake_vs_Helloworld WIN32 ${sources})

#include_directories(../SeikoBinaryFile)
#set (EXTRA_LIBS ${EXTRA_LIBS} SeikoBinaryFile)


add_executable(AnalogClock  ${CURRENT_INCLUDE} ${CURRENT_SOURCES} ${CURRENT_FORM} )

# also tell CMake to link with the libraries from the line 14
# otherwise it'll think that you wanted to find those just for fun and won't link them

#target_link_libraries(
#    ${CMAKE_PROJECT_NAME}
#    Qt5::Widgets
#    )

target_link_libraries(
    AnalogClock
   # Qt5::Gui
    Qt5::Widgets
    ${EXTRA_LIBS}
    )



