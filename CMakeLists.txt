cmake_minimum_required (VERSION 3.10)
project(parakeet-qt VERSION 1.0.2 LANGUAGES CXX)

set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

if (WIN32)
    set(CMAKE_DEBUG_POSTFIX "d")
endif()

find_package(Parakeet REQUIRED)
find_package(Qt5 COMPONENTS Widgets Core SerialPort REQUIRED)

set(PROJECT_SOURCE
    src/main.cpp
    src/mainwindow.cpp
    src/mainwindow.h
    src/mainwindow.ui
    src/ScanDataViewModel.h
    src/ScanDataViewModel.cpp
    src/QCustomGraphicsView.h
    src/QCustomGraphicsView.cpp
)

add_executable(parakeet-viewer ${PROJECT_SOURCE})
target_include_directories(parakeet-viewer PRIVATE Parakeet::Parakeet src/)
target_link_libraries(parakeet-viewer PRIVATE Qt5::Widgets Qt5::SerialPort Parakeet::Parakeet)
