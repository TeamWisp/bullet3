INCLUDE_DIRECTORIES(
  ${BULLET_PHYSICS_SOURCE_DIR}/src
  ${BULLET_PHYSICS_SOURCE_DIR}/examples
  ${BULLET_PHYSICS_SOURCE_DIR}/examples/ThirdPartyLibs
  ${BULLET_PHYSICS_SOURCE_DIR}/examples/ThirdPartyLibs/enet/include
  ${BULLET_PHYSICS_SOURCE_DIR}/examples/ThirdPartyLibs/clsocket/src
)


SET(
  bullet_c_api_SRCS
  ../../examples/SharedMemory/plugins/stablePDPlugin/SpAlg.cpp
  ../../examples/SharedMemory/plugins/stablePDPlugin/SpAlg.h
  ../../examples/SharedMemory/plugins/stablePDPlugin/Shape.cpp
  ../../examples/SharedMemory/plugins/stablePDPlugin/Shape.h
  ../../examples/SharedMemory/plugins/stablePDPlugin/RBDUtil.cpp
  ../../examples/SharedMemory/plugins/stablePDPlugin/RBDUtil.h
  ../../examples/SharedMemory/plugins/stablePDPlugin/RBDModel.cpp
  ../../examples/SharedMemory/plugins/stablePDPlugin/RBDModel.h
  ../../examples/SharedMemory/plugins/stablePDPlugin/MathUtil.cpp
  ../../examples/SharedMemory/plugins/stablePDPlugin/MathUtil.h
  ../../examples/SharedMemory/plugins/stablePDPlugin/KinTree.cpp
  ../../examples/SharedMemory/plugins/stablePDPlugin/KinTree.h
  ../../examples/SharedMemory/plugins/stablePDPlugin/BulletConversion.cpp
  ../../examples/SharedMemory/plugins/stablePDPlugin/BulletConversion.h
  ../../examples/SharedMemory/plugins/collisionFilterPlugin/collisionFilterPlugin.cpp
  ../../examples/SharedMemory/plugins/pdControlPlugin/pdControlPlugin.cpp
  ../../examples/SharedMemory/plugins/pdControlPlugin/pdControlPlugin.h
  ../../examples/SharedMemory/b3RobotSimulatorClientAPI_NoDirect.cpp
  ../../examples/SharedMemory/b3RobotSimulatorClientAPI_NoDirect.h
  ../../examples/SharedMemory/IKTrajectoryHelper.cpp
  ../../examples/SharedMemory/IKTrajectoryHelper.h
  ../../examples/ExampleBrowser/InProcessExampleBrowser.cpp
  ../../examples/SharedMemory/plugins/tinyRendererPlugin/tinyRendererPlugin.cpp
  ../../examples/SharedMemory/plugins/tinyRendererPlugin/tinyRendererPlugin.h
  ../../examples/SharedMemory/plugins/tinyRendererPlugin/TinyRendererVisualShapeConverter.cpp
  ../../examples/SharedMemory/plugins/tinyRendererPlugin/TinyRendererVisualShapeConverter.h
  ../../examples/OpenGLWindow/SimpleCamera.cpp
  ../../examples/OpenGLWindow/SimpleCamera.h
  ../../examples/TinyRenderer/geometry.cpp
  ../../examples/TinyRenderer/model.cpp
  ../../examples/TinyRenderer/tgaimage.cpp
  ../../examples/TinyRenderer/our_gl.cpp
  ../../examples/TinyRenderer/TinyRenderer.cpp
  ../../examples/SharedMemory/InProcessMemory.cpp
  ../../examples/SharedMemory/PhysicsClient.cpp
  ../../examples/SharedMemory/PhysicsClient.h
  ../../examples/SharedMemory/PhysicsServer.cpp
  ../../examples/SharedMemory/PhysicsServer.h
  ../../examples/SharedMemory/PhysicsServerExample.cpp
  ../../examples/SharedMemory/PhysicsServerExampleBullet2.cpp
  ../../examples/SharedMemory/SharedMemoryInProcessPhysicsC_API.cpp
  ../../examples/SharedMemory/PhysicsServerSharedMemory.cpp
  ../../examples/SharedMemory/PhysicsServerSharedMemory.h
  ../../examples/SharedMemory/PhysicsDirect.cpp
  ../../examples/SharedMemory/PhysicsDirect.h
  ../../examples/SharedMemory/PhysicsDirectC_API.cpp
  ../../examples/SharedMemory/PhysicsDirectC_API.h
  ../../examples/SharedMemory/PhysicsServerCommandProcessor.cpp
  ../../examples/SharedMemory/PhysicsServerCommandProcessor.h
  ../../examples/SharedMemory/b3PluginManager.cpp
  ../../examples/SharedMemory/b3PluginManager.h
  ../../examples/SharedMemory/PhysicsClientSharedMemory.cpp
  ../../examples/SharedMemory/PhysicsClientSharedMemory.h
  ../../examples/SharedMemory/PhysicsClientSharedMemory_C_API.cpp
  ../../examples/SharedMemory/PhysicsClientSharedMemory_C_API.h
  ../../examples/SharedMemory/PhysicsClientC_API.cpp
  ../../examples/SharedMemory/PhysicsClientC_API.h
  ../../examples/SharedMemory/Win32SharedMemory.cpp
  ../../examples/SharedMemory/Win32SharedMemory.h
  ../../examples/SharedMemory/PosixSharedMemory.cpp
  ../../examples/SharedMemory/PosixSharedMemory.h
  ../../examples/Utils/b3ResourcePath.cpp
  ../../examples/Utils/b3ResourcePath.h
  ../../examples/Utils/RobotLoggingUtil.cpp
  ../../examples/Utils/RobotLoggingUtil.h
  ../../examples/ThirdPartyLibs/tinyxml2/tinyxml2.cpp
  ../../examples/ThirdPartyLibs/Wavefront/tiny_obj_loader.cpp
  ../../examples/ThirdPartyLibs/Wavefront/tiny_obj_loader.h
  ../../examples/ThirdPartyLibs/stb_image/stb_image.cpp
  ../../examples/ThirdPartyLibs/stb_image/stb_image_write.cpp
  ../../examples/Importers/ImportColladaDemo/LoadMeshFromCollada.cpp
  ../../examples/Importers/ImportObjDemo/LoadMeshFromObj.cpp
  ../../examples/Importers/ImportObjDemo/Wavefront2GLInstanceGraphicsShape.cpp
  ../../examples/Importers/ImportMJCFDemo/BulletMJCFImporter.cpp
  ../../examples/Importers/ImportURDFDemo/BulletUrdfImporter.cpp
  ../../examples/Importers/ImportURDFDemo/MyMultiBodyCreator.cpp
  ../../examples/Importers/ImportURDFDemo/URDF2Bullet.cpp
  ../../examples/Importers/ImportURDFDemo/UrdfParser.cpp
  ../../examples/Importers/ImportURDFDemo/urdfStringSplit.cpp
  ../../examples/Importers/ImportMeshUtility/b3ImportMeshUtility.cpp
  ../../examples/MultiThreading/b3PosixThreadSupport.cpp
  ../../examples/MultiThreading/b3Win32ThreadSupport.cpp
  ../../examples/MultiThreading/b3ThreadSupportInterface.cpp
)
IF(BUILD_PYBULLET_CLSOCKET)
  ADD_DEFINITIONS(-DBT_ENABLE_CLSOCKET)
ENDIF(BUILD_PYBULLET_CLSOCKET)

IF(WIN32)
  IF(BUILD_PYBULLET_ENET)
    ADD_DEFINITIONS(-DWIN32 -DBT_ENABLE_ENET)
  ENDIF(BUILD_PYBULLET_ENET)
  IF(BUILD_PYBULLET_CLSOCKET)
    ADD_DEFINITIONS(-DWIN32)
  ENDIF(BUILD_PYBULLET_CLSOCKET)

ELSE(WIN32)
  IF(BUILD_PYBULLET_ENET)
    ADD_DEFINITIONS(-DHAS_SOCKLEN_T -DBT_ENABLE_ENET)
  ENDIF(BUILD_PYBULLET_ENET)

  IF(BUILD_PYBULLET_CLSOCKET)
    ADD_DEFINITIONS(${OSDEF})
  ENDIF(BUILD_PYBULLET_CLSOCKET)
ENDIF(WIN32)

IF(BUILD_PYBULLET_ENET)
  SET(
    bullet_c_api_SRCS
    ${bullet_c_api_SRCS}
    ../../examples/SharedMemory/PhysicsClientUDP.cpp
    ../../examples/SharedMemory/PhysicsClientUDP_C_API.cpp
    ../../examples/SharedMemory/PhysicsClientUDP.h
    ../../examples/SharedMemory/PhysicsClientUDP_C_API.h
    ../../examples/ThirdPartyLibs/enet/win32.c
    ../../examples/ThirdPartyLibs/enet/unix.c
    ../../examples/ThirdPartyLibs/enet/callbacks.c
    ../../examples/ThirdPartyLibs/enet/compress.c
    ../../examples/ThirdPartyLibs/enet/host.c
    ../../examples/ThirdPartyLibs/enet/list.c
    ../../examples/ThirdPartyLibs/enet/packet.c
    ../../examples/ThirdPartyLibs/enet/peer.c
    ../../examples/ThirdPartyLibs/enet/protocol.c
  )
ENDIF(BUILD_PYBULLET_ENET)

IF(BUILD_PYBULLET_CLSOCKET)
  SET(
    bullet_c_api_SRCS
    ${bullet_c_api_SRCS}
    ../../examples/SharedMemory/PhysicsClientTCP.cpp
    ../../examples/SharedMemory/PhysicsClientTCP.h
    ../../examples/SharedMemory/PhysicsClientTCP_C_API.cpp
    ../../examples/SharedMemory/PhysicsClientTCP_C_API.h
    ../../examples/ThirdPartyLibs/clsocket/src/SimpleSocket.cpp
    ../../examples/ThirdPartyLibs/clsocket/src/ActiveSocket.cpp
    ../../examples/ThirdPartyLibs/clsocket/src/PassiveSocket.cpp
  )
ENDIF()

ADD_LIBRARY(bullet_c_api SHARED ${bullet_c_api_SRCS})

SET_TARGET_PROPERTIES(bullet_c_api PROPERTIES PREFIX "")
SET_TARGET_PROPERTIES(bullet_c_api PROPERTIES POSTFIX "")

SET_TARGET_PROPERTIES(bullet_c_api PROPERTIES VERSION ${BULLET_VERSION})
SET_TARGET_PROPERTIES(bullet_c_api PROPERTIES SOVERSION ${BULLET_VERSION})
SET_TARGET_PROPERTIES(bullet_c_api PROPERTIES DEBUG_POSTFIX "_d")

IF(WIN32)
  IF(BUILD_PYBULLET_ENET OR BUILD_PYBULLET_CLSOCKET)
    TARGET_LINK_LIBRARIES(bullet_c_api ws2_32)
  ENDIF(BUILD_PYBULLET_ENET OR BUILD_PYBULLET_CLSOCKET)
ENDIF(WIN32)


TARGET_LINK_LIBRARIES(
  bullet_c_api
  BulletExampleBrowserLib
  BulletFileLoader
  BulletWorldImporter
  BulletSoftBody
  BulletDynamics
  BulletCollision
  BulletInverseDynamicsUtils
  BulletInverseDynamics
  LinearMath
  OpenGLWindow
  gwen
  BussIK
  Bullet3Common
)

TARGET_LINK_LIBRARIES(bullet_c_api ${OPENGL_gl_LIBRARY} ${OPENGL_glu_LIBRARY})

IF (INSTALL_LIBS)
	IF (NOT INTERNAL_CREATE_DISTRIBUTABLE_MSVC_PROJECTFILES)
		#INSTALL of other files requires CMake 2.6
		IF (${CMAKE_MAJOR_VERSION}.${CMAKE_MINOR_VERSION} GREATER 2.5)
			IF (APPLE AND BUILD_SHARED_LIBS AND FRAMEWORK)
				INSTALL(TARGETS bullet_c_api DESTINATION lib)
			ELSE (APPLE AND BUILD_SHARED_LIBS AND FRAMEWORK)
				INSTALL(TARGETS bullet_c_api RUNTIME DESTINATION bin
								LIBRARY DESTINATION lib${LIB_SUFFIX}
								ARCHIVE DESTINATION lib${LIB_SUFFIX})

			ENDIF (APPLE AND BUILD_SHARED_LIBS AND FRAMEWORK)
		ENDIF (${CMAKE_MAJOR_VERSION}.${CMAKE_MINOR_VERSION} GREATER 2.5)

		IF (APPLE AND BUILD_SHARED_LIBS AND FRAMEWORK)
			SET_TARGET_PROPERTIES(bullet_c_api PROPERTIES FRAMEWORK true)

			SET_TARGET_PROPERTIES(bullet_c_api PROPERTIES PUBLIC_HEADER "${Root_HDRS}")
			# Have to list out sub-directories manually:


		ENDIF (APPLE AND BUILD_SHARED_LIBS AND FRAMEWORK)
	ENDIF (NOT INTERNAL_CREATE_DISTRIBUTABLE_MSVC_PROJECTFILES)
ENDIF (INSTALL_LIBS)
