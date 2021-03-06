#
# Copyright (C) 2015 MediaTek Inc.
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License version 2 as
# published by the Free Software Foundation.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
# GNU General Public License for more details.
#

ccflags-y += -I$(srctree)/drivers/misc/mediatek/video/include/ \
             -I$(srctree)/drivers/misc/mediatek/video/common/ \
             -I$(srctree)/drivers/misc/mediatek/video/$(MTK_PLATFORM)/videox/ \
             -I$(srctree)/drivers/misc/mediatek/base/power/mt6755/ \
             -I$(srctree)/drivers/misc/mediatek/lcm/inc \
             -I$(srctree)/drivers/misc/mediatek/m4u/$(MTK_PLATFORM)/ \
             -I$(srctree)/drivers/misc/mediatek/mmp/

ccflags-y += -I$(srctree)/drivers/misc/mediatek/video/$(MTK_PLATFORM)/dispsys

ifeq (y, $(filter y, $(CONFIG_MACH_MT6763) $(CONFIG_MACH_MT6799) $(CONFIG_MACH_MT6759) $(CONFIG_MACH_MT6758) $(CONFIG_MACH_MT6775) $(CONFIG_MACH_MT6771) $(CONFIG_MACH_MT6739)))
ccflags-y += \
		-I$(srctree)/drivers/misc/mediatek/cmdq/v3/ \
		-I$(srctree)/drivers/misc/mediatek/cmdq/v3/$(MTK_PLATFORM)/
else
ccflags-y += \
		-I$(srctree)/drivers/misc/mediatek/cmdq/v2/ \
		-I$(srctree)/drivers/misc/mediatek/cmdq/v2/$(MTK_PLATFORM)/
endif

obj-y += ddp_color.o

ifeq ($(strip $(CONFIG_MTK_PQ_COLOR_MODE)),"MDP")
    ccflags-y += -DDISP_COLOR_OFF
else ifeq ($(strip $(CONFIG_MTK_PQ_COLOR_MODE)),"OFF")
    ccflags-y += -DDISP_COLOR_OFF
endif

ifneq (y, $(filter y, $(CONFIG_MACH_MT6580) $(CONFIG_MACH_MT6570)))
    ccflags-y += -DCCORR_SUPPORT
endif

ifeq (y, $(filter y, $(CONFIG_MACH_MT6797) $(CONFIG_MACH_MT6757) $(CONFIG_MACH_MT6799) \
			$(CONFIG_MACH_MT6759) $(CONFIG_MACH_MT6763) $(CONFIG_MACH_MT6758) $(CONFIG_MACH_MT6775) $(CONFIG_MACH_MT6771)))
    ccflags-y += -DCOLOR_2_1
endif

ifeq (y, $(filter y, $(CONFIG_MACH_MT6757) $(CONFIG_MACH_MT6759) $(CONFIG_MACH_MT6799) \
			$(CONFIG_MACH_MT6763) $(CONFIG_MACH_MT6758) $(CONFIG_MACH_MT6775) $(CONFIG_MACH_MT6771)))
    ccflags-y += -DCOLOR_3_0
endif

ifeq (y, $(filter y, $(CONFIG_MACH_MT6799)))
    ccflags-y += -DSUPPORT_HDR
endif

ifeq (y, $(filter y, $(CONFIG_MACH_MT6771) $(CONFIG_MACH_MT6775)))
    ccflags-y += -DSUPPORT_MDP_AAL
endif

ifeq (y, $(filter y, $(CONFIG_MACH_MT6797) $(CONFIG_MACH_MT6799) $(CONFIG_MACH_MT6763) \
             $(CONFIG_MACH_MT6758) $(CONFIG_MACH_MT6775) $(CONFIG_MACH_MT6771)))
    ccflags-y += -DSUPPORT_ULTRA_RESOLUTION
endif

ifeq ($(strip $(CONFIG_MTK_PQ_COLOR_MODE)),"MDP")
    ccflags-y += -DMDP_COLOR_ON
else ifeq ($(strip $(CONFIG_MTK_PQ_COLOR_MODE)),"DISP_MDP")
    ccflags-y += -DDISP_MDP_COLOR_ON
else ifeq ($(strip $(CONFIG_MTK_PQ_COLOR_MODE)),"DISP")
    ccflags-y += -DDISP_COLOR_ON
endif

ifeq ($(strip $(CONFIG_MTK_LCM_PHYSICAL_ROTATION)),"180")
    ccflags-y += -DLCM_PHYSICAL_ROTATION_180
else ifeq ($(strip $(CONFIG_MTK_LCM_PHYSICAL_ROTATION)),"270")
    ccflags-y += -DLCM_PHYSICAL_ROTATION_270
else ifeq ($(strip $(CONFIG_MTK_LCM_PHYSICAL_ROTATION_HW)),y)
    ccflags-y += -DLCM_PHYSICAL_ROTATION_180
endif
