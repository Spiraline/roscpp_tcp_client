cmake_minimum_required(VERSION 3.5)
project(rosbridge_client)

add_compile_options(-std=c++17)

## Find catkin macros and libraries
## if COMPONENTS list like find_package(catkin REQUIRED COMPONENTS xyz)
## is used, also find other catkin packages
find_package(catkin REQUIRED COMPONENTS
  roscpp
  std_msgs
  nlohmann_json
)

find_package(Boost 1.65.1 COMPONENTS serialization REQUIRED)

catkin_package(
  #INCLUDE_DIRS include
  #LIBRARIES ${PROJECT_NAME}
  #CATKIN_DEPENDS roscpp std_msgs 
  #DEPENDS system_lib
)

include_directories(
  include
  ${catkin_INCLUDE_DIRS}
)

add_executable(rosbridge_tcp_talker src/rosbridge_tcp_talker.cpp)
target_link_libraries(rosbridge_tcp_talker
  ${catkin_LIBRARIES}
  ${Boost_LIBRARIES}
)

add_executable(rosbridge_tcp_listener src/rosbridge_tcp_listener.cpp)
target_link_libraries(rosbridge_tcp_listener
  ${catkin_LIBRARIES}
  ${Boost_LIBRARIES}
)

add_executable(rosbridge_websocket_talker src/rosbridge_websocket_talker.cpp)
target_link_libraries(rosbridge_websocket_talker
  ${catkin_LIBRARIES}
  ${Boost_LIBRARIES}
)

add_executable(rosbridge_websocket_listener src/rosbridge_websocket_listener.cpp)
target_link_libraries(rosbridge_websocket_listener
  ${catkin_LIBRARIES}
  ${Boost_LIBRARIES}
)