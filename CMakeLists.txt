cmake_minimum_required(VERSION 3.3)

PROJECT("pv-datetime-filter")

message(STATUS ${ParaView_DIR})
message(STATUS ${CMAKE_PREFIX_PATH})


FIND_PACKAGE(ParaView REQUIRED)
INCLUDE(${PARAVIEW_USE_FILE})


INCLUDE_DIRECTORIES(
  "${PROJECT_SOURCE_DIR}"
  "${PROJECT_BINARY_DIR}"
)

find_package(Boost
             1.54.0
             COMPONENTS
             date_time
             REQUIRED)

include_directories(${BOOST_INCLUDE_PATH} ${Boost_INCLUDE_DIR})  #new and old format for incl dir path

SET(PLUGIN_NAME TimeAnnotate)

ADD_PARAVIEW_PLUGIN(
  ${PLUGIN_NAME}
  "1.0" 
  SERVER_MANAGER_XML
    vtkDateTimeAnnotation.xml
  SERVER_MANAGER_SOURCES
    vtkDateTimeAnnotation.cxx
#  SERVER_SOURCES
#    Extra-sources.cpp
)

TARGET_LINK_LIBRARIES(${PLUGIN_NAME}) #other link here as required

install (TARGETS ${PLUGIN_NAME} DESTINATION "lib")