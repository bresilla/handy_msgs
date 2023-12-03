cmake_minimum_required(VERSION 3.8)
project(handy_msgs)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(rosidl_default_generators REQUIRED)
find_package(nav_msgs REQUIRED)
find_package(std_msgs REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(sensor_msgs REQUIRED)

# self._gps2ecef = self.create_service(NavSatFix, '/fix/convert/gps2ecef', self.gps2ecef)
# self._ecef2gps = self.create_service(Odometry, '/fix/convert/ecef2gps', self.ecef2gps)

# self._ecef2enu = self.create_service(Odometry, '/fix/convert/ecef2enu', self.ecef2enu)
# self._enu2ecef = self.create_service(Odometry, '/fix/convert/enu2ecef', self.enu2ecef)

# self._gps2enu = self.create_service(NavSatFix, '/fix/convert/gps2enu', self.gps2enu)
# self._enu2gps = self.create_service(Odometry, '/fix/convert/enu2gps', self.enu2gps)

rosidl_generate_interfaces(${PROJECT_NAME}
  "action/Nav.action"
  "action/Obstacle.action"
  "srv/Reset.srv"
  "srv/Datum.srv"
  "srv/Gps2Ecef.srv"
  "srv/Ecef2Gps.srv"
  "srv/Ecef2Enu.srv"
  "srv/Enu2Ecef.srv"
  "srv/Gps2Enu.srv"
  "srv/Enu2Gps.srv"
  "srv/Threshold.srv"
  "msg/Float32Stamped.msg"
  DEPENDENCIES nav_msgs std_msgs geometry_msgs sensor_msgs
)

if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  # the following line skips the linter which checks for copyrights
  # comment the line when a copyright and license is added to all source files
  set(ament_cmake_copyright_FOUND TRUE)
  # the following line skips cpplint (only works in a git repo)
  # comment the line when this package is in a git repo and when
  # a copyright and license is added to all source files
  set(ament_cmake_cpplint_FOUND TRUE)
  ament_lint_auto_find_test_dependencies()
endif()

ament_package()
