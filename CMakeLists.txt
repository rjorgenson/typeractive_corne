# Custom ZMK module for typeractive_corne
# Overrides usb_hid.c to default to Boot Protocol for KVM compatibility

if(CONFIG_ZMK_USB)
    # Mark the original usb_hid.c as header-only so it won't be compiled
    set_source_files_properties(${ZEPHYR_BASE}/../zmk/app/src/usb_hid.c
        PROPERTIES HEADER_FILE_ONLY TRUE)

    # Add our custom version (path relative to module root)
    target_sources(app PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/app/src/usb_hid.c)
endif()
