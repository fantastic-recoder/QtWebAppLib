project( QtWebApp )
cmake_minimum_required( VERSION 2.6 )
set ( CMAKE_BUILD_TYPE Release )
add_definitions ( -Wall )

# Find includes in corresponding build directories
set(CMAKE_INCLUDE_CURRENT_DIR ON)
# Instruct CMake to run moc automatically when needed.
#set(CMAKE_AUTOMOC ON)

find_package ( Qt5Core REQUIRED )
find_package ( Qt5Network REQUIRED )

include_directories (
	${CMAKE_SOURCE_DIR} ${CMAKE_CURRENT_BINARY_DIR}
	${QT_QTCORE_INCLUDE_DIR}
	${QT_QTNETWORK_INCLUDE_DIR}
	)


set ( QtWebApp_HDRS
	 httpserver/httpglobal.h 
	 httpserver/httplistener.h 
	 httpserver/httpconnectionhandler.h 
	 httpserver/httpconnectionhandlerpool.h 
	 httpserver/httprequest.h 
	 httpserver/httpresponse.h 
	 httpserver/httpcookie.h 
	 httpserver/httprequesthandler.h 
	 httpserver/httpsession.h 
	 httpserver/httpsessionstore.h 
	 httpserver/staticfilecontroller.h	
)

set ( QtWebApp_SRCS
	 httpserver/httpglobal.cpp 
	 httpserver/httplistener.cpp 
	 httpserver/httpconnectionhandler.cpp 
	 httpserver/httpconnectionhandlerpool.cpp 
	 httpserver/httprequest.cpp 
	 httpserver/httpresponse.cpp 
	 httpserver/httpcookie.cpp 
	 httpserver/httprequesthandler.cpp 
	 httpserver/httpsession.cpp 
	 httpserver/httpsessionstore.cpp 
	 httpserver/staticfilecontroller.cpp	
)

add_library ( QtWebApp SHARED ${QtWebApp_SRCS} ${UIS} ${RSCS} ${TRS} ${MOCS} )
target_link_libraries ( QtWebApp  ${QT_QTCORE_LIBRARY} )
