cmake_minimum_required(VERSION 3.1)
# Enable C++17
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED TRUE)
project( PeopleCounter )
find_package( OpenCV REQUIRED )
add_executable( PeopleCounter PeopleCounter.cpp )
target_link_libraries( PeopleCounter ${OpenCV_LIBS} )
add_custom_target(run)
add_custom_command( TARGET run
	POST_BUILD COMMAND ./PeopleCounter -i input-airport-480x360.mp4)
add_custom_target(run-hog)
add_custom_command( TARGET run-hog
	POST_BUILD COMMAND ./PeopleCounter -i input-airport-fhd.mp4 -t hog)
