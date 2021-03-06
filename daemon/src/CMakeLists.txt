cmake_minimum_required (VERSION 2.6) 
project (daemon) 

SET(CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/Modules)
FIND_PACKAGE(Boost REQUIRED COMPONENTS system chrono thread)
FIND_PACKAGE(Rabbitmqc REQUIRED)
FIND_PACKAGE(SimpleAmqpClient REQUIRED)
FIND_PACKAGE(OpenCV REQUIRED)

INCLUDE_DIRECTORIES(SYSTEM ${Rabbitmqc_INCLUDE_DIRS})
INCLUDE_DIRECTORIES(SYSTEM ${SimpleAmqpClient_INCLUDE_DIRS})
INCLUDE_DIRECTORIES(${Boost_INCLUDE_DIRS})
LINK_DIRECTORIES(${Boost_LIBRARY_DIRS})

ADD_EXECUTABLE(daemon main.cpp)
TARGET_LINK_LIBRARIES(daemon ${Rabbitmqc_LIBRARY} ${Boost_LIBRARIES} ${SimpleAmqpClient_LIBRARY} ${OpenCV_LIBS})
