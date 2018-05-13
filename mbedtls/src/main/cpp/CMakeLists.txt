
#
# Copyright (C) The Android Open Source Project
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#      http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#

# Generate one static lib and one shared lib, copy them into
# ${project_dir}/distribution for other indepdendent applications
# to use.
cmake_minimum_required(VERSION 3.4.1)
set(MY_LIBNAME mbedtls)

set(CMAKE_VERBOSE_MAKEFILE on)
set(ENABLE_TESTING OFF)
set(USE_STATIC_MBEDTLS_LIBRARY ON)

add_subdirectory(mbedtls)

# copy out the lib binary... need to leave the static lib around to pass gradle check
#set(distribution_DIR ${CMAKE_CURRENT_SOURCE_DIR}/../../../../distribution)
#add_custom_command(TARGET ${MY_LIBNAME} POST_BUILD
#                   COMMAND "${CMAKE_COMMAND}" -E
#                   copy "${CMAKE_CURRENT_SOURCE_DIR}/mbedtls/library/libmbedcrypto.a" "${distribution_DIR}/${MY_LIBNAME}/lib/"
#                   COMMENT "Copying ${MY_LIBNAME} to output directory")

# copy out lib header file...
#add_custom_command(TARGET ${MY_LIBNAME} POST_BUILD
#                   COMMAND "${CMAKE_COMMAND}" -E
#                   copy "${CMAKE_CURRENT_SOURCE_DIR}/mbedtls/include" "${distribution_DIR}/${MY_LIBNAME}/"
#                   COMMENT "Copying ${MY_LIBNAME} to output directory")
