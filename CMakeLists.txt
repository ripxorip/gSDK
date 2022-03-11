project(gimbal_tester)

cmake_minimum_required(VERSION 3.5)

set(MAVLINK_INCLUDES
    "${CMAKE_CURRENT_SOURCE_DIR}/src/mavlink/include/mavlink/v2.0")

set(MAVLINK_SRC
    "${CMAKE_CURRENT_SOURCE_DIR}/src")

###############################################################################
#### INCLUDES #################################################################
###############################################################################

include_directories(${CMAKE_CURRENT_SOURCE_DIR}
                    ${CMAKE_CURRENT_SOURCE_DIR}/src
                    ${MAVLINK_INCLUDES}
                    )

###############################################################################
#### DEPENDENCIES #############################################################
###############################################################################

###############################################################################
#### GENERATE OUTPUT ##########################################################
###############################################################################

set(GSDK_APP_SRC
    gimbal_tester.cpp
    ${MAVLINK_SRC}/gimbal_interface.cpp
    ${MAVLINK_SRC}/serial_port.cpp
)

add_executable(gimbal_tester ${GSDK_APP_SRC})

find_package( Threads )
target_link_libraries(gimbal_tester
                      ${CMAKE_THREAD_LIBS_INIT}
                      )

#install(TARGETS
#        gSDK
#        RUNTIME DESTINATION usr/bin/gSDK)

# add_subdirectory("${CMAKE_CURRENT_SOURCE_DIR}/examples")
