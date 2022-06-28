################################################################################
#
# Copyright 2017-2018 NVIDIA Corporation.  All rights reserved.
#
# Please refer to the NVIDIA end user license agreement (EULA) associated
# with this source code for terms and conditions that govern your use of
# this software. Any use, reproduction, disclosure, or distribution of
# this software and related documentation outside the terms of the EULA
# is strictly prohibited.
#
################################################################################

include ../../common.mk

# Target rules
all: build

build: AppEncGL AppEncGL_gears

LDFLAGS += -lX11 -lGL -lglut -lGLEW -lEGL -lGLESv2
INCLUDES += -I/home/plin/Works/WinD/gitlab.freedesktop.org/mesa/demos/src/util

NvEncoder.o: ../../NvCodec/NvEncoder/NvEncoder.cpp ../../NvCodec/NvEncoder/NvEncoder.h
	$(GCC) $(CCFLAGS) $(INCLUDES) -o $@ -c $<

NvEncoderGL.o: ../../NvCodec/NvEncoder/NvEncoderGL.cpp ../../NvCodec/NvEncoder/NvEncoderGL.h \
               ../../NvCodec/NvEncoder/NvEncoder.h
	$(GCC) $(CCFLAGS) $(INCLUDES) -o $@ -c $<

AppEncGL.o: AppEncGL.cpp ../../NvCodec/NvEncoder/NvEncoderGL.h \
            ../../NvCodec/NvEncoder/NvEncoder.h ../../Utils/NvCodecUtils.h \
            ../../Utils/NvEncoderCLIOptions.h ../../Utils/Logger.h
	$(GCC) $(CCFLAGS) $(INCLUDES) -o $@ -c $<

AppEncGL_gears.o: AppEncGL_gears.cpp ../../NvCodec/NvEncoder/NvEncoderGL.h \
            ../../NvCodec/NvEncoder/NvEncoder.h ../../Utils/NvCodecUtils.h \
            ../../Utils/NvEncoderCLIOptions.h ../../Utils/Logger.h
	$(GCC) $(CCFLAGS) $(INCLUDES) -o $@ -c $<

AppEncGL: AppEncGL.o NvEncoder.o NvEncoderGL.o
	$(GCC) $(CCFLAGS) -o $@ $^ $(LDFLAGS)

AppEncGL_gears: AppEncGL_gears.o NvEncoder.o NvEncoderGL.o
	$(GCC) $(CCFLAGS) -o $@ $^ $(LDFLAGS)

clean:
	rm -rf AppEncGL AppEncGL.o NvEncoder.o NvEncoderGL.o
