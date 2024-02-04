# Copyright (c) 2017 Erwin Rol <erwin@erwinrol.com>
#
# SPDX-License-Identifier: Apache-2.0

zephyr_sources(soc/system_hc32f460.c)
zephyr_sources(drivers/src/hc32_ll.c)
zephyr_sources(drivers/src/hc32_ll_utility.c)
zephyr_sources(drivers/src/hc32_ll_clk.c)
zephyr_sources(drivers/src/hc32_ll_efm.c)
zephyr_sources(drivers/src/hc32_ll_icg.c)
zephyr_sources(drivers/src/hc32_ll_sram.c)
zephyr_sources_ifdef(CONFIG_USE_HC32_DDL_GPIO drivers/src/hc32_ll_gpio.c)
