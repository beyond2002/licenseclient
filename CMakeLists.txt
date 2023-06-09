cmake_minimum_required(VERSION 3.6)

SET(CMAKE_DISABLE_SOURCE_CHANGES ON)
SET(CMAKE_DISABLE_IN_SOURCE_BUILD ON)

IF(NOT LCC_PROJECT_NAME)
		message(STATUS "You should define a variable LCC_PROJECT_NAME containing the name of the software you want to add a license to.\n \
		 A mock project named `DEFAULT` has been added for you.\n \
		 This project name should correspond to an existing project name in licensecc library. use `lcc project create` to create new projects.") 
	set(LCC_PROJECT_NAME "DEFAULT" CACHE STRING "Project name (name of the software for which you want to issue a license)") 
ENDIF(NOT LCC_PROJECT_NAME)

project (licenseclient CXX)
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
SET(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_CURRENT_SOURCE_DIR}/cmake/")

find_package(licensecc 2.0.0 REQUIRED)
message(STATUS "LicenseCC found " ${licensecc_DIR})
add_executable(licensecheck src/licensecheck.cpp)
cmake_policy(SET CMP0028 NEW)
target_link_libraries(licensecheck licensecc::licensecc_static)

#run open-license-manager tests
INCLUDE(CTest)