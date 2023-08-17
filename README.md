ZMK Config
==========

This repository hosts the configuration for the "Prime 17" keyboard, a split
wireless keyboard with a wired hub, based around a nice!nano MCU.

The following commands assume this repo is cloned to `zmk-config` and that the
builds will be produced in `hub`, `left` and `right` directories respectively.

The hub:

```sh
$ west build -d hub -b nice_nano_v2 -- \
    -DSHIELD=prime17 -DZMK_CONFIG=zmk-config \
    -DCONFIG_ZMK_SPLIT=y \
    -DCONFIG_ZMK_SPLIT_ROLE_CENTRAL=y \
    -DCONFIG_ZMK_SPLIT_BLE_CENTRAL_PERIPHERALS=2
```

Left:
```sh
$ west build -d left -b nice_nano_v2 -- \
    -DSHIELD="prime17 nice_view_adapter nice_view" -DZMK_CONFIG=zmk-config\
    -DCONFIG_ZMK_SPLIT=y -DDTS_EXTRA_CPPFLAGS="-DPRIME17_LEFT"
```

Right:
```sh
$ west build -d right -b nice_nano_v2 -- \
    -DSHIELD="prime17 nice_view_adapter nice_view" -DZMK_CONFIG=zmk-config\
    -DCONFIG_ZMK_SPLIT=y -DDTS_EXTRA_CPPFLAGS="-DPRIME17_RIGHT"
```
