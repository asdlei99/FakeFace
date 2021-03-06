#TBB library
include_directories(${TBB_ROOT_DIR}/include)

include_directories(${BOOST_INCLUDE_DIR})

SET(SOURCE
    src/Face_utils.cpp
	src/FaceAnalyser.cpp
	src/SVM_dynamic_lin.cpp
	src/SVM_static_lin.cpp
	src/SVR_dynamic_lin_regressors.cpp
	src/SVR_static_lin_regressors.cpp
	src/GazeEstimation.cpp
)

SET(HEADERS
    include/Face_utils.h	
	include/FaceAnalyser.h
	include/SVM_dynamic_lin.h
	include/SVM_static_lin.h
	include/SVR_dynamic_lin_regressors.h
	include/SVR_static_lin_regressors.h
	include/GazeEstimation.h
)

include_directories(./include)
include_directories(${FACEANALYSER_SOURCE_DIR}/include)
include_directories(../LandmarkDetector/include)

add_definitions(-DDLIB_HAVE_SSE2
	-DDLIB_HAVE_SSE3
	-DDLIB_HAVE_SSE4
	-D_UNICODE
	-DUNICODE
)

add_library( FaceAnalyser ${SOURCE} ${HEADERS})

install (TARGETS FaceAnalyser DESTINATION lib)
install (FILES ${HEADERS} DESTINATION include/OpenFace)
