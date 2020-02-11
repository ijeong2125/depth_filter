cmake_minimum_required(VERSION 2.8.3)
project(go_stopbycolor)

find_package(catkin REQUIRED COMPONENTS
  geometry_msgs
  message_generation
  roscpp
  std_msgs
)

## Generate messages in the 'msg' folder
add_message_files(
   FILES
   color_vel.msg
)
 generate_messages(
   DEPENDENCIES
   geometry_msgs   std_msgs
 )


catkin_package(
  INCLUDE_DIRS include
  LIBRARIES go_stopbycolor
  CATKIN_DEPENDS geometry_msgs roscpp std_msgs
  )


include_directories(
# include
  ${catkin_INCLUDE_DIRS}
)

add_executable(change_cmd_publisher src/change_cmd_publisher.cpp)
add_dependencies(change_cmd_publisher ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})
target_link_libraries(change_cmd_publisher
   ${catkin_LIBRARIES}
 )

#  add_dependencies(change_cmd_subscriber ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})
#  add_executable(change_cmd_subscriber src/change_cmd_subscriber.cpp)
#  target_link_libraries(change_cmd_subscriber
#    ${catkin_LIBRARIES}
#  )
