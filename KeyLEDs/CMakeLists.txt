# Project Needs a name ofcourse
project(plasma-keyleds)

# Find the required Libaries
find_package(KDE4 REQUIRED)
include(KDE4Defaults)


add_definitions (${QT_DEFINITIONS} ${KDE4_DEFINITIONS})
include_directories(
   ${CMAKE_SOURCE_DIR}
   ${CMAKE_BINARY_DIR}
   ${KDE4_INCLUDES}
   )

# We add our source code here
set(keyleds_SRCS source/singletonstate.cpp source/dialogconfig.cpp source/dialogabout.cpp source/ledstatus.cpp source/keyleds.cpp)

# Adicionado por David - FZ
kde4_add_ui_files(keyleds_SRCS source/ui/DialogAbout.ui source/ui/DialogConfig.ui)

# Now make sure all files get to the right place
kde4_add_plugin(plasma_applet_keyleds ${keyleds_SRCS})
target_link_libraries(plasma_applet_keyleds
                      ${KDE4_PLASMA_LIBS} ${KDE4_KDEUI_LIBS})

install(TARGETS plasma_applet_keyleds
        DESTINATION ${PLUGIN_INSTALL_DIR})

install(FILES plasma-applet-keyleds.desktop
        DESTINATION ${SERVICES_INSTALL_DIR})

add_subdirectory(source)