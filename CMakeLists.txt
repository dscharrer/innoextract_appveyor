project(innoextract_appveyor)

cmake_minimum_required(VERSION 2.8.5...3.19)

# Change CMAKE_LIBRARY_ARCHITECTURE to ensure the right libs are used
if(CMAKE_CL_64)
	set(CMAKE_LIBRARY_ARCHITECTURE "x64")
else()
	set(CMAKE_LIBRARY_ARCHITECTURE "x86")
endif()

set(libs "${CMAKE_CURRENT_LIST_DIR}/libs")
set(CMAKE_PREFIX_PATH
	"${libs}/liblzma"
)

if(DEFINED CMAKE_FIND_ROOT_PATH)
	# Need to be able to find these using absolute paths
	if(CMAKE_FIND_ROOT_PATH_MODE_LIBRARY STREQUAL NEVER)
		set(CMAKE_FIND_ROOT_PATH_MODE_LIBRARY LAST)
	endif()
	if(CMAKE_FIND_ROOT_PATH_MODE_INCLUDE STREQUAL NEVER)
		set(CMAKE_FIND_ROOT_PATH_MODE_INCLUDE LAST)
	endif()
endif()

add_subdirectory("innoextract")
