cmake_minimum_required(VERSION 3.8)
project(arduinobot_python_firmware)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()


find_package(ament_cmake REQUIRED)
find_package(ament_cmake_python REQUIRED)  	#python
find_package(rclpy REQUIRED)			#python

install(PROGRAMS				#python
  ${PROJECT_NAME}/simple_serial_transmitter.py	#python
  DESTINATION lib/${PROJECT_NAME}		#python
)						#python

if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  set(ament_cmake_copyright_FOUND TRUE)
  set(ament_cmake_cpplint_FOUND TRUE)
  ament_lint_auto_find_test_dependencies()
endif()

ament_package()
