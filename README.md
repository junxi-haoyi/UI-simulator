# usage
install sdl on your pc better on Linux

```cmake
sudo apt update && sudo apt install -y build-essential libsdl2-dev
```


build with cmake

```
sudo apt install cmake
```

Get project

```
git clone --recursive git@github.com:junxi-haoyi/UI-simulator.git
```

comment out line 47 of the CMake file in the lv_drivers folder

content as follows

```cmake
 configure_file("${CMAKE_SOURCE_DIR}/lv-drivers.pc.in" lv-drivers.pc @ONLY)

 install(
   FILES "${CMAKE_BINARY_DIR}/lv-drivers.pc"
   DESTINATION "${LIB_INSTALL_DIR}/pkgconfig/")
```

change the name of file called lv_drv_conf_template.h to lv_drv_conf.h in lv_drivers folder

set `if 0` to `if 1` in line 11

