cmake_minimum_required( VERSION 3.16 )

if( NOT CMAKE_CROSSCOMPILING )
	include_directories( SYSTEM "${BZIP2_INCLUDE_DIR}" "${LZMA_INCLUDE_DIR}" ${CMAKE_SOURCE_DIR}/libraries/miniz)
	SET(CMAKE_EXE_LINKER_FLAGS  "${CMAKE_EXE_LINKER_FLAGS} -Wl,-rpath,$ORIGIN/../../libraries/miniz")
	add_executable( zipdir
		zipdir.c )
	target_link_libraries( zipdir miniz ${BZIP2_LIBRARIES} lzma )
	set( CROSS_EXPORTS ${CROSS_EXPORTS} zipdir PARENT_SCOPE )
endif()
