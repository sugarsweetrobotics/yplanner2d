set(srcs yplanner2d.c)

include_directories(../include)

set(headers)
foreach(hdr ${hdrs})
  set(headers ${headers}  "${hdr}")
endforeach(hdr)

add_library(${PROJECT_NAME} SHARED ${srcs} ${headers})

if(WIN32)
  add_definitions("/D _YPLAN_USE_STATIC")
endif(WIN32)

add_library(${PROJECT_NAME}_static STATIC ${srcs} ${headers})
target_link_libraries(${PROJECT_NAME}_static)

install(TARGETS ${PROJECT_NAME} ${PROJECT_NAME}_static
    EXPORT ${PROJECT_NAME} DESTINATION ${LIB_INSTALL_DIR})
