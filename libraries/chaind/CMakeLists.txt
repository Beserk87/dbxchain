
file(GLOB HEADERS "*.hpp")

set(sources net.cpp chaind.cpp  ${HEADERS})

add_library( chaind ${sources} ${HEADERS} )
target_link_libraries( chaind PRIVATE graphene_chain fc jsoncpp ${CMAKE_DL_LIBS} ${PLATFORM_SPECIFIC_LIBS} )
target_include_directories( chaind PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}" )

install( TARGETS
   chaind

   RUNTIME DESTINATION bin
   LIBRARY DESTINATION lib
   ARCHIVE DESTINATION lib
)
install( FILES ${HEADERS} DESTINATION "." )
