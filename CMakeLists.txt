# Copyright 2018-2020 Camilo Higuita <milo.h@aol.com>
# Copyright 2018-2020 Nitrux Latinoamericana S.C.
#
# SPDX-License-Identifier: GPL-3.0-or-later

cmake_minimum_required(VERSION 3.16)

set(MAUI_DEFAULT_CONF_VERSION 1.0.0)

project(maui_default_conf VERSION ${MAUI_DEFAULT_CONF_VERSION})

find_package(ECM ${REQUIRED_KF5_VERSION} REQUIRED NO_MODULE)
set(CMAKE_MODULE_PATH "${CMAKE_CURRENT_SOURCE_DIR}/cmake" ${ECM_MODULE_PATH})

if(UNIX AND NOT APPLE AND NOT ANDROID)
    include(KDEInstallDirs)
    include(KDECMakeSettings)
endif()

include(FeatureSummary)

install(FILES mauiproject.conf DESTINATION $ENV{HOME}/.config/org.kde.maui/)
install(FILES cask.conf DESTINATION $ENV{HOME}/.config/maui/)

feature_summary(WHAT ALL FATAL_ON_MISSING_REQUIRED_PACKAGES)
