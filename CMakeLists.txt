cmake_minimum_required(VERSION 3.0.0)
project(quickflux)

set(CMAKE_INCLUDE_CURRENT_DIR ON)

find_package(Qt5Core REQUIRED)
find_package(Qt5Quick REQUIRED)
find_package(Qt5Qml REQUIRED)

include_directories(${Qt5Qml_INCLUDE_DIRS})

qt5_wrap_cpp(moc 
    priv/qflistener.h
    priv/qfappscriptrunnable.h
    priv/qfappscriptdispatcherwrapper.h
    priv/qfhook.h
    priv/qfmiddlewareshook.h
    qfactioncreator.h
    qfappdispatcher.h
    qfapplistener.h
    qfapplistenergroup.h
    qfappscript.h
    qfappscriptgroup.h
    qffilter.h
    qfkeytable.h
    qfmiddleware.h
    qfmiddlewarelist.h
    qfobject.h
    qfstore.h
    qfhydrate.h
)

set(SOURCES
    ${moc}
    qfapplistener.cpp
    qfappdispatcher.cpp
    qfappscript.cpp
    qfappscriptrunnable.cpp
    qfappscriptdispatcherwrapper.cpp
    qflistener.cpp
    qfqmltypes.cpp
    qfapplistenergroup.cpp
    qfappscriptgroup.cpp
    qffilter.cpp
    qfkeytable.cpp
    priv/qfsignalproxy.cpp
    priv/qfhook.cpp
    priv/qfmiddlewareshook.cpp
    priv/quickfluxfunctions.cpp
    qfactioncreator.cpp
    qfmiddleware.cpp
    qfmiddlewarelist.cpp
    qfobject.cpp
    qfstore.cpp
    qfhydrate.cpp

)

set(HEADERS
    qfappdispatcher.h
    qfapplistener.h
    qfappscript.h
    priv/qfappscriptrunnable.h
    priv/qfappscriptdispatcherwrapper.h
    priv/qflistener.h
    qfapplistenergroup.h
    qfappscriptgroup.h
    qffilter.h
    qfkeytable.h
    priv/qfsignalproxy.h
    qfactioncreator.h
    QFAppDispatcher
    QFKeyTable
    QuickFlux
)


add_library(quickflux ${SOURCES})

target_link_libraries(quickflux PUBLIC Qt5::Qml Qt5::Quick Qt5::Core)
target_include_directories(quickflux PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})
