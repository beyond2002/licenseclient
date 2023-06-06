
ADD_EXECUTABLE(lccinspector inspector.cpp )

target_link_libraries(lccinspector 
     licensecc_static)

install(TARGETS lccinspector RUNTIME DESTINATION bin/${LCC_PROJECT_NAME})
