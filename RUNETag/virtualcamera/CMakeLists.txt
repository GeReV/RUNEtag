PROJECT( virtualcamera )


IF( VERBOSE_FLAG  )
ADD_DEFINITIONS( -DVERBOSE )
ENDIF()


SET( VIRTUALCAMERA_SRCS 
	Camera.cpp
	VirtualCamera.cpp
	)
	 
SET( VIRTUALCAMERA_INCL 
	Camera.h
	VirtualCamera.h
	 )
	 

INCLUDE_DIRECTORIES(.
					${OpenCV_INCLUDE_DIRS}
					)

INSTALL( FILES "VirtualCamera.h" DESTINATION "include/virtualcamera" )
ADD_LIBRARY( ${PROJECT_NAME} ${VIRTUALCAMERA_SRCS} ${VIRTUALCAMERA_INCL} )		
INSTALL( TARGETS ${PROJECT_NAME} DESTINATION lib PERMISSIONS OWNER_READ OWNER_WRITE OWNER_EXECUTE GROUP_READ GROUP_EXECUTE WORLD_READ WORLD_EXECUTE )


ADD_EXECUTABLE( ${PROJECT_NAME}_test main.cpp VirtualCamera.h )
TARGET_LINK_LIBRARIES(  ${PROJECT_NAME}_test ${PROJECT_NAME} ${OpenCV_LIBS}  )
INSTALL( TARGETS ${PROJECT_NAME}_test DESTINATION bin PERMISSIONS OWNER_READ OWNER_WRITE OWNER_EXECUTE GROUP_READ GROUP_EXECUTE WORLD_READ WORLD_EXECUTE )
