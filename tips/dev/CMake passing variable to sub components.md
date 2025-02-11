---
creation date: 2025-08-02 12:12:12
tags:
  - dev/tips
  - dev/platform/esp
  - dev/language/cmake
language:
  - cmake
---
To add pass an environment variable from the `cmake` command and have that environment variable be propagated across sub components CMake file:

In the main CMakeLists.txt

```cmake
idf_build_set_property(COMPILE_OPTIONS "-DBUILD_TARGET=${BUILD_TARGET}" APPEND)  
project("${PROJECT_BIN}") 
```
 
In the sub components
```
idf_build_get_property(_options COMPILE_OPTIONS)  
if(_options MATCHES "-DBUILD_TARGET=PSI")  
  message("------ Truck SDO type set to PSI")  
  set(TRUCK_SDO_SRC "canOpenTruckSdoPsi.c"  "./profile/truckOD.c")  
elseif(_options MATCHES "-DBUILD_TARGET=EURO")  
  message("------ Truck SDO type set to EURO")  
  set(TRUCK_SDO_SRC "canOpenTruckSdoEuro.c"  "./profile/euroTruckOD.c")  
else()  
  message(${_options})    
  message(FATAL_ERROR "## invalid compiler -DBUILD_TARGET")  
endif()  
```

```bash
#!/bin/sh  
#  
# REM File to do IDF operations for PSI comms firmware build  
#  
idf.py -B\build_psi -DBUILD_TARGET=PSI $@
```