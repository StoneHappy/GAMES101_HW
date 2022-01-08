cmake_minimum_required(VERSION 3.16)
project( HW_03 )

set(CMAKE_CXX_STANDARD 17)

file(GLOB PROJECT_HEADERS           *.h
                                    *.hpp
                                    )
file(GLOB PROJECT_SOURCES           *.cpp
                                    )

add_executable( ${PROJECT_NAME} 
        ${PROJECT_SOURCES} 
        ${PROJECT_HEADERS}
        )
target_link_libraries( ${PROJECT_NAME} ${OpenCV_LIBS} )

target_include_directories(${PROJECT_NAME} PUBLIC
                           ${GAMES101_HW_SOURCE_DIR}/vendors/eigen-3.4.0/ 
                           ${OpenCV_INCLUDE_DIRS}
             )
add_custom_command(
TARGET ${PROJECT_NAME} POST_BUILD
COMMAND ${CMAKE_COMMAND} -E copy_directory ${CMAKE_CURRENT_SOURCE_DIR}/models/ $<TARGET_FILE_DIR:${PROJECT_NAME}>/models/)