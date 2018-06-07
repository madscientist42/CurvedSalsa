cmake_minimum_required(VERSION 2.6)

PROJECT(curvedsalsa)

FILE(GLOB source_files *.c *.cpp *.h *.inl)

ADD_EXECUTABLE(curvedsalsa 
	${source_files}
)

IF (WIN32)
	TARGET_LINK_LIBRARIES(curvedsalsa optimized "cryptopp/Win32/output/release/cryptlib")
	TARGET_LINK_LIBRARIES(curvedsalsa debug "cryptopp/Win32/output/debug/cryptlib")

	STRING(REPLACE	"/MDd"	"/MTd"	CMAKE_CXX_FLAGS_DEBUG	${CMAKE_CXX_FLAGS_DEBUG})	
	STRING(REPLACE	"/MD"	"/MT"	CMAKE_CXX_FLAGS_DEBUG	${CMAKE_CXX_FLAGS_DEBUG})	
ELSE (WIN32)
	TARGET_LINK_LIBRARIES(curvedsalsa dl)
ENDIF (WIN32)
