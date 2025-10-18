# Custom ZMK module for typeractive_corne
# Overrides usb_hid.c to default to Boot Protocol for KVM compatibility

if(CONFIG_ZMK_USB AND CONFIG_ZMK_USB_BOOT)
    target_sources(app PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/app/src/usb_hid.c)
endif()
