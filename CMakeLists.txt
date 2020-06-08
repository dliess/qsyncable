cmake_minimum_required(VERSION 3.5)

project(testJsonListModel LANGUAGES CXX)

set(CMAKE_INCLUDE_CURRENT_DIR ON)

set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(Qt5 COMPONENTS Core Quick REQUIRED)

set (HEADERS
   "qsdiffrunner.h"
   "qspatch.h"
   "qspatchable.h"
   "qslistmodel.h"
   "qsuuid.h"
   "priv/qsdiffrunneralgo_p.h"
   "priv/qstree.h"
   "priv/qstreenode.h"
   "qsjsonlistmodel.h"
   "QSDiffRunner"
   "QSListModel"
   "qsyncablefunctions.h"
   "qsyncableqmlwrapper.h"
   "priv/qsalgotypes_p.h"
   "priv/qsimmutablewrapper_p.h"
   "priv/qsfastdiffrunneralgo_p.h"
   "qsfastdiffrunner.h"
)

set(SOURCES
   "qsdiffrunner.cpp"
   "qspatch.cpp"
   "qslistmodel.cpp"
   "qsuuid.cpp"
   "qsdiffrunneralgo.cpp"
   "qstree.cpp"
   "qstreenode.cpp"
   "qsjsonlistmodel.cpp"
   "qsyncableqmltypes.cpp"
   "qsyncablefunctions.cpp"
   "qsyncableqmlwrapper.cpp"
)

#add_library(qsyncable STATIC ${SOURCES} ${HEADERS})
## Somehow the global register functions only work when added as object library 
add_library(qsyncable OBJECT ${SOURCES} ${HEADERS})

target_include_directories(qsyncable PUBLIC ${CMAKE_CURRENT_LIST_DIR})
target_link_libraries(qsyncable
  PUBLIC Qt5::Core 
  PUBLIC Qt5::Quick
)
