# cmake_minimum_required(VERSION 2.8.3)
# project(serial)

# # 设置C++标准
# set(CMAKE_CXX_STANDARD 11)

# # 查找系统库
# if(APPLE)
#     find_library(IOKIT_LIBRARY IOKit)
#     find_library(FOUNDATION_LIBRARY Foundation)
# endif()

# # 设置输出目录
# set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
# set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
# set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

# ## Sources
# set(serial_SRCS
#     src/serial.cc
#     include/serial/serial.h
#     include/serial/v8stdint.h
# )
# if(APPLE)
#     # If OSX
#     list(APPEND serial_SRCS src/impl/unix.cc)
#     list(APPEND serial_SRCS src/impl/list_ports/list_ports_osx.cc)
# elseif(UNIX)
#     # If unix
#     list(APPEND serial_SRCS src/impl/unix.cc)
#     list(APPEND serial_SRCS src/impl/list_ports/list_ports_linux.cc)
# else()
#     # If windows
#     list(APPEND serial_SRCS src/impl/win.cc)
#     list(APPEND serial_SRCS src/impl/list_ports/list_ports_win.cc)
# endif()

# ## Add serial library
# add_library(${PROJECT_NAME} ${serial_SRCS})

# # 链接系统库
# if(APPLE)
#     target_link_libraries(${PROJECT_NAME} ${FOUNDATION_LIBRARY} ${IOKIT_LIBRARY})
# elseif(UNIX AND NOT APPLE)
#     target_link_libraries(${PROJECT_NAME} rt pthread)
# else()
#     target_link_libraries(${PROJECT_NAME} setupapi)
# endif()

# # 设置包含目录
# target_include_directories(${PROJECT_NAME} PUBLIC
#     $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
#     $<INSTALL_INTERFACE:include>
# )

# ## Example executable
# add_executable(serial_example examples/serial_example.cc)
# target_link_libraries(serial_example ${PROJECT_NAME})

# ## Install targets
# install(TARGETS ${PROJECT_NAME}
#     EXPORT serialTargets
#     ARCHIVE DESTINATION lib
#     LIBRARY DESTINATION lib
#     RUNTIME DESTINATION bin
# )

# install(TARGETS serial_example
#     RUNTIME DESTINATION bin
# )

# ## Install headers
# install(DIRECTORY include/serial
#     DESTINATION include
#     FILES_MATCHING PATTERN "*.h"
# )

# # 创建并安装配置和目标文件
# install(EXPORT serialTargets
#     FILE serialTargets.cmake
#     NAMESPACE serial::
#     DESTINATION lib/cmake/serial
# )

# # 创建配置文件
# include(CMakePackageConfigHelpers)
# configure_package_config_file(
#     "${CMAKE_CURRENT_SOURCE_DIR}/cmake/serialConfig.cmake.in"
#     "${CMAKE_CURRENT_BINARY_DIR}/cmake/serialConfig.cmake"
#     INSTALL_DESTINATION lib/cmake/serial
# )

# # 安装配置文件
# install(FILES "${CMAKE_CURRENT_BINARY_DIR}/cmake/serialConfig.cmake"
#     DESTINATION lib/cmake/serial
# )

# ## Tests
# option(BUILD_TESTING "Build tests" OFF)
# if(BUILD_TESTING)
#     enable_testing()
#     add_subdirectory(tests)
# endif()



# cmake_minimum_required(VERSION 2.8.3)
# project(serial)

# # Find catkin
# find_package(catkin REQUIRED)

# if(APPLE)
#     find_library(IOKIT_LIBRARY IOKit)
#     find_library(FOUNDATION_LIBRARY Foundation)
# endif()

# if(UNIX AND NOT APPLE)
#     # If Linux, add rt and pthread
#     set(rt_LIBRARIES rt)
#     set(pthread_LIBRARIES pthread)
#     catkin_package(
#         LIBRARIES ${PROJECT_NAME}
#         INCLUDE_DIRS include
#         DEPENDS rt pthread
#     )
# else()
#     # Otherwise normal call
#     catkin_package(
#         LIBRARIES ${PROJECT_NAME}
#         INCLUDE_DIRS include
#     )
# endif()

# ## Sources
# set(serial_SRCS
#     src/serial.cc
#     include/serial/serial.h
#     include/serial/v8stdint.h
# )
# if(APPLE)
#     # If OSX
#     list(APPEND serial_SRCS src/impl/unix.cc)
#     list(APPEND serial_SRCS src/impl/list_ports/list_ports_osx.cc)
# elseif(UNIX)
#     # If unix
#     list(APPEND serial_SRCS src/impl/unix.cc)
#     list(APPEND serial_SRCS src/impl/list_ports/list_ports_linux.cc)
# else()
#     # If windows
#     list(APPEND serial_SRCS src/impl/win.cc)
#     list(APPEND serial_SRCS src/impl/list_ports/list_ports_win.cc)
# endif()

# ## Add serial library
# add_library(${PROJECT_NAME} ${serial_SRCS})
# if(APPLE)
#     target_link_libraries(${PROJECT_NAME} ${FOUNDATION_LIBRARY} ${IOKIT_LIBRARY})
# elseif(UNIX)
#     target_link_libraries(${PROJECT_NAME} rt pthread)
# else()
#     target_link_libraries(${PROJECT_NAME} setupapi)
# endif()

# ## Uncomment for example
# add_executable(serial_example examples/serial_example.cc)
# add_dependencies(serial_example ${PROJECT_NAME})
# target_link_libraries(serial_example ${PROJECT_NAME})

# ## Include headers
# include_directories(include)

# ## Install executable
# install(TARGETS ${PROJECT_NAME}
#     ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
#     LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
#     RUNTIME DESTINATION ${CATKIN_GLOBAL_BIN_DESTINATION}
# )

# ## Install headers
# install(FILES include/serial/serial.h include/serial/v8stdint.h
#   DESTINATION ${CATKIN_GLOBAL_INCLUDE_DESTINATION}/serial)

# ## Tests
# if(CATKIN_ENABLE_TESTING)
#     add_subdirectory(tests)
# endif()


# cmake_minimum_required(VERSION 2.8.3)
# project(serial)

# # 设置C++标准
# set(CMAKE_CXX_STANDARD 11)

# # 查找系统库
# if(APPLE)
#     find_library(IOKIT_LIBRARY IOKit)
#     find_library(FOUNDATION_LIBRARY Foundation)
# endif()

# # 设置输出目录
# set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
# set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
# set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

# ## Sources
# set(serial_SRCS
#     src/serial.cc
#     include/serial/serial.h
#     include/serial/v8stdint.h
# )
# if(APPLE)
#     # If OSX
#     list(APPEND serial_SRCS src/impl/unix.cc)
#     list(APPEND serial_SRCS src/impl/list_ports/list_ports_osx.cc)
# elseif(UNIX)
#     # If unix
#     list(APPEND serial_SRCS src/impl/unix.cc)
#     list(APPEND serial_SRCS src/impl/list_ports/list_ports_linux.cc)
# else()
#     # If windows
#     list(APPEND serial_SRCS src/impl/win.cc)
#     list(APPEND serial_SRCS src/impl/list_ports/list_ports_win.cc)
# endif()

# ## Add serial library
# add_library(${PROJECT_NAME} ${serial_SRCS})

# # 链接系统库
# if(APPLE)
#     target_link_libraries(${PROJECT_NAME} ${FOUNDATION_LIBRARY} ${IOKIT_LIBRARY})
# elseif(UNIX AND NOT APPLE)
#     target_link_libraries(${PROJECT_NAME} rt pthread)
# else()
#     target_link_libraries(${PROJECT_NAME} setupapi)
# endif()

# # 设置包含目录
# target_include_directories(${PROJECT_NAME} PUBLIC
#     $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
#     $<INSTALL_INTERFACE:include>
# )

# ## Example executable
# add_executable(serial_example examples/serial_example.cc)
# target_link_libraries(serial_example ${PROJECT_NAME})

# ## Install targets
# install(TARGETS ${PROJECT_NAME}
#     EXPORT serialTargets
#     ARCHIVE DESTINATION lib
#     LIBRARY DESTINATION lib
#     RUNTIME DESTINATION bin
# )

# install(TARGETS serial_example
#     RUNTIME DESTINATION bin
# )

# ## Install headers
# install(DIRECTORY include/serial
#     DESTINATION include
#     FILES_MATCHING PATTERN "*.h"
# )

# ## Tests
# option(BUILD_TESTING "Build tests" OFF)
# if(BUILD_TESTING)
#     enable_testing()
#     add_subdirectory(tests)
# endif()


cmake_minimum_required(VERSION 3.5)
project(serial VERSION 1.0.0 LANGUAGES CXX)

# 设置安装路径变量
set(CMAKE_INSTALL_INCLUDEDIR include)
set(CMAKE_INSTALL_LIBDIR lib)

# 根据平台配置源文件和依赖
set(serial_SRCS
    src/serial.cc
)

if(APPLE)
    list(APPEND serial_SRCS 
        src/impl/unix.cc
        src/impl/list_ports/list_ports_osx.cc
    )
    find_library(IOKIT_LIBRARY IOKit)
    find_library(FOUNDATION_LIBRARY Foundation)
elseif(UNIX)
    list(APPEND serial_SRCS 
        src/impl/unix.cc
        src/impl/list_ports/list_ports_linux.cc
    )
    set(rt_LIBRARIES rt)
    set(pthread_LIBRARIES pthread)
else()
    list(APPEND serial_SRCS 
        src/impl/win.cc
        src/impl/list_ports/list_ports_win.cc
    )
    set(setupapi_LIBRARIES setupapi)
endif()

# 创建主库
add_library(${PROJECT_NAME} SHARED ${serial_SRCS})
target_include_directories(${PROJECT_NAME} PUBLIC
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
    $<INSTALL_INTERFACE:${CMAKE_INSTALL_INCLUDEDIR}>
)

# 平台特定链接库
if(APPLE)
    target_link_libraries(${PROJECT_NAME} PRIVATE 
        ${FOUNDATION_LIBRARY} ${IOKIT_LIBRARY})
elseif(UNIX)
    target_link_libraries(${PROJECT_NAME} PRIVATE 
        ${rt_LIBRARIES} ${pthread_LIBRARIES})
else()
    target_link_libraries(${PROJECT_NAME} PRIVATE 
        ${setupapi_LIBRARIES})
endif()

# 添加示例程序
add_executable(serial_example examples/serial_example.cc)
target_link_libraries(serial_example ${PROJECT_NAME})

# 安装配置
install(TARGETS ${PROJECT_NAME} EXPORT serialTargets
    ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
    RUNTIME DESTINATION bin
)

install(FILES 
    include/serial/serial.h 
    include/serial/v8stdint.h
    DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}/serial
)

# 生成并安装配置文件
include(CMakePackageConfigHelpers)

# 创建版本文件
write_basic_package_version_file(
    serialConfigVersion.cmake
    VERSION ${PROJECT_VERSION}
    COMPATIBILITY AnyNewerVersion
)

# 创建配置文件
configure_package_config_file(
    ${CMAKE_CURRENT_SOURCE_DIR}/cmake/serialConfig.cmake.in
    ${CMAKE_CURRENT_BINARY_DIR}/serialConfig.cmake
    INSTALL_DESTINATION ${CMAKE_INSTALL_LIBDIR}/cmake/serial
)

# 安装导出目标和配置文件
install(EXPORT serialTargets
    FILE serialTargets.cmake
    NAMESPACE serial::
    DESTINATION ${CMAKE_INSTALL_LIBDIR}/cmake/serial
)

install(FILES
    ${CMAKE_CURRENT_BINARY_DIR}/serialConfig.cmake
    ${CMAKE_CURRENT_BINARY_DIR}/serialConfigVersion.cmake
    DESTINATION ${CMAKE_INSTALL_LIBDIR}/cmake/serial
)