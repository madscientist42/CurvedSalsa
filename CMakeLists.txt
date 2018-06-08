cmake_minimum_required(VERSION 3.0)

PROJECT(curvedsalsa)

FIND_PACKAGE(Boost COMPONENTS program_options)

FILE(GLOB source_files *.c *.cpp *.h *.inl)

ADD_EXECUTABLE(curvedsalsa 
	${source_files}
)


MESSAGE(STATUS ${Boost_LIBRARIES})

TARGET_LINK_LIBRARIES(curvedsalsa ${Boost_LIBRARIES})


