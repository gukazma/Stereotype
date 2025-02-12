set(TARGET_NAME Worker)
find_package(glog CONFIG REQUIRED)


file(GLOB_RECURSE CPP_HEAD_FILES  ${CMAKE_CURRENT_SOURCE_DIR}/*.h)
file(GLOB_RECURSE CPP_SOUCE_FILES  ${CMAKE_CURRENT_SOURCE_DIR}/*.cpp)

source_group(TREE ${CMAKE_CURRENT_LIST_DIR} FILES ${CPP_HEAD_FILES} ${CPP_SOUCE_FILES})

add_executable(${TARGET_NAME} ${CPP_HEAD_FILES} ${CPP_SOUCE_FILES})
set_target_properties(${TARGET_NAME} PROPERTIES FOLDER Apps)
# Link dependencies    
target_link_libraries(${TARGET_NAME} PUBLIC
colmap_exe
          )
if(DEFINED glog_VERSION_MAJOR)
target_compile_definitions(${TARGET_NAME} PRIVATE
          "-DGLOG_VERSION_MAJOR=${glog_VERSION_MAJOR}"
          "-DGLOG_VERSION_MINOR=${glog_VERSION_MINOR}"
      )
endif()
          
target_include_directories(${TARGET_NAME} PUBLIC  ${CMAKE_SOURCE_DIR}/Vendors/colmap/src)