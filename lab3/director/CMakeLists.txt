cmake_minimum_required(VERSION 3.0)

project(director)


set(SOURCE_FILES director_cli.cpp director_agent.cpp director.cpp director_acceptor.cpp ../signal_handler.cpp ../sender.cpp play.cpp player.cpp ../string_util.cpp ../common.cpp)
set(HEADER_FILES director_agent.h director_acceptor.h director.h ../sender.h play.h player.h ../string_util.h ../common.h ../signal_handler.h)

add_executable(director ${SOURCE_FILES} ${HEADER_FILES})

if(WIN32)
	target_link_libraries(director ACEd)
else(WIN32)
	target_link_libraries(director ACE)
endif(WIN32)

if(${CMAKE_SYSTEM} MATCHES "Linux")
  target_link_libraries(director pthread)
endif(${CMAKE_SYSTEM} MATCHES "Linux")
