# Custom ZMK module for typeractive_corne
# Overrides usb_hid.c to default to Boot Protocol for KVM compatibility

if(CONFIG_ZMK_USB)
    # Remove the original usb_hid.c from the build
    get_target_property(APP_SOURCES app SOURCES)
    list(FILTER APP_SOURCES EXCLUDE REGEX ".*usb_hid\\.c$")
    set_property(TARGET app PROPERTY SOURCES ${APP_SOURCES})

    # Add our custom version
    target_sources(app PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/app/src/usb_hid.c)
endif()
