# SPDX-FileCopyrightText: 2024 Deskflow Developers
# SPDX-FileCopyrightText: 2024 Symless Ltd
# SPDX-License-Identifier: MIT

set(target gui)

set(CMAKE_INCLUDE_CURRENT_DIR ON)

if(APPLE)
  set (platform_sources
    OSXHelpers.h
    OSXHelpers.mm
  )
endif()

add_library(${target} STATIC
  ${platform_sources}
  Constants.h
  Diagnostic.cpp
  Diagnostic.h
  DotEnv.cpp
  DotEnv.h
  EnvVars.h
  FileTail.cpp
  FileTail.h
  Logger.cpp
  Logger.h
  Messages.cpp
  Messages.h
  StringUtils.h
  StyleUtils.h
  Styles.h
  config/IServerConfig.h
  config/Screen.cpp
  config/Screen.h
  config/ScreenConfig.cpp
  config/ScreenConfig.h
  config/ScreenList.cpp
  config/ScreenList.h
  core/ClientConnection.cpp
  core/ClientConnection.h
  core/CommandProcess.cpp
  core/CommandProcess.h
  core/CoreProcess.cpp
  core/CoreProcess.h
  core/ServerConnection.cpp
  core/ServerConnection.h
  core/ServerMessage.cpp
  core/ServerMessage.h
  core/WaylandWarnings.cpp
  core/WaylandWarnings.h
  ipc/DaemonIpcClient.cpp
  ipc/DaemonIpcClient.h
  proxy/QNetworkAccessManagerProxy.cpp
  proxy/QNetworkAccessManagerProxy.h
  proxy/QProcessProxy.cpp
  proxy/QProcessProxy.h
  tls/TlsCertificate.cpp
  tls/TlsCertificate.h
  tls/TlsUtility.cpp
  tls/TlsUtility.h
  validators/AliasValidator.cpp
  validators/AliasValidator.h
  validators/ComputerNameValidator.cpp
  validators/ComputerNameValidator.h
  validators/EmptyStringValidator.cpp
  validators/EmptyStringValidator.h
  validators/IStringValidator.cpp
  validators/IStringValidator.h
  validators/LineEditValidator.cpp
  validators/LineEditValidator.h
  validators/ScreenDuplicationsValidator.cpp
  validators/ScreenDuplicationsValidator.h
  validators/ScreenNameValidator.cpp
  validators/ScreenNameValidator.h
  validators/SpacesValidator.cpp
  validators/SpacesValidator.h
  validators/ValidationError.cpp
  validators/ValidationError.h
)

target_link_libraries(
  ${target}
  common
  platform
  Qt6::Core
  Qt6::Widgets
  Qt6::Network)

if(WIN32)
  target_link_libraries(
    ${target}
    base
    arch
    net
  )
endif()
