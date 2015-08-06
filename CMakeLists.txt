# Copyright (c) 2014 CNRS
# Author: Florent Lamiraux
#
# This file is part of hpp-universal-robot.
# hpp-universal-robot is free software: you can redistribute it
# and/or modify it under the terms of the GNU Lesser General Public
# License as published by the Free Software Foundation, either version
# 3 of the License, or (at your option) any later version.
#
# hpp-universal-robot is distributed in the hope that it will be
# useful, but WITHOUT ANY WARRANTY; without even the implied warranty
# of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
# General Lesser Public License for more details.  You should have
# received a copy of the GNU Lesser General Public License along with
# hpp-universal-robot.  If not, see
# <http://www.gnu.org/licenses/>.

# Requires at least CMake 2.6 to configure the package.
CMAKE_MINIMUM_REQUIRED(VERSION 2.6)

INCLUDE(cmake/base.cmake)
INCLUDE(cmake/python.cmake)

SET(PROJECT_NAME hpp_universal_robot)
SET(PROJECT_DESCRIPTION
  "Data specific to ur5 and 10 robots for hpp-corbaserver")
SET(PROJECT_URL "")

SETUP_PROJECT()

FINDPYTHON()

# Catkin stuff
FIND_PACKAGE(catkin)
CATKIN_PACKAGE()

ADD_REQUIRED_DEPENDENCY ("hpp-corbaserver >= 3")

INSTALL(FILES
  ${PROJECT_SOURCE_DIR}/src/hpp/corbaserver/ur5/robot.py
  ${PROJECT_SOURCE_DIR}/src/hpp/corbaserver/ur5/__init__.py
  DESTINATION ${PYTHON_SITELIB}/hpp/corbaserver/ur5
)

INSTALL(FILES
  ${PROJECT_SOURCE_DIR}/src/hpp/corbaserver/manipulation/ur5/robot.py
  ${PROJECT_SOURCE_DIR}/src/hpp/corbaserver/manipulation/ur5/__init__.py
  DESTINATION ${PYTHON_SITELIB}/hpp/corbaserver/manipulation/ur5
)

INSTALL(FILES
  ${PROJECT_SOURCE_DIR}/share/ur_description/srdf/ur5.srdf
  ${PROJECT_SOURCE_DIR}/share/ur_description/srdf/ur5_joint_limited_robot.srdf
  DESTINATION ${CMAKE_INSTALL_DATAROOTDIR}/ur_description/srdf
)

INSTALL(FILES
  ${PROJECT_SOURCE_DIR}/launch/ur5.launch
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/launch
)

INSTALL(FILES
  ${PROJECT_SOURCE_DIR}/share/rviz/config.rviz 
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/rviz
)

SETUP_PROJECT_FINALIZE()
