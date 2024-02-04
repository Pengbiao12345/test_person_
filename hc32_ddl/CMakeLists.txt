# Makefile - Cube SDK
#
# Copyright (c) 2016 Linaro Limited
#
# SPDX-License-Identifier: Apache-2.0

#add_library(CUBE INTERFACE)
string(TOUPPER ${CONFIG_SOC} _HC32_CPU)
string(REPLACE "X" "x" CUBE_CPU ${_HC32_CPU})

# Cub uses the CPU name to expose SOC-specific attributes of a specific
# peripheral.
# It also requires USE_HAL_DRIVER to be define in order to benefit from
# Cube HAL and LL APIs
zephyr_compile_definitions(
  -D${_HC32_CPU}
  -DUSE_DDL_DRIVER
  )

set(hc32_socs
  hc32f460
  )

foreach(hc32_soc ${hc32_socs})
  string(TOUPPER ${hc32_soc} soc_to_upper)
  if(CONFIG_SOC_${soc_to_upper})
    zephyr_include_directories(
	  ${hc32_soc}/soc
	  ${hc32_soc}/drivers/include
	  )

    add_subdirectory(${hc32_soc})
  endif()
endforeach()
