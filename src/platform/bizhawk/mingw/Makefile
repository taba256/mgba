CC ?= gcc
RM ?= rm
CP ?= cp

MACHINE = $(shell $(CC) -dumpmachine)

ifneq (,$(findstring i686,$(MACHINE)))
    $(error 32 bit build no longer supported)
else ifneq (,$(findstring x86_64,$(MACHINE)))
    ARCH = 64
else
    $(error Unknown arch)
endif

MAKEFILE_DIR := $(shell dirname $(realpath $(lastword $(MAKEFILE_LIST))))
ROOT_DIR := $(MAKEFILE_DIR)/../../..
OBJ_DIR := $(MAKEFILE_DIR)/obj

LDFLAGS_32 = -static-libgcc
LDFLAGS_64 =
LDFLAGS = -shared $(LDFLAGS_$(ARCH)) $(CCFLAGS)

DEST_32 = ../../../../../output/dll
DEST_64 = ../../../../../output/dll

PLAT_SRCS += \
	$(ROOT_DIR)/platform/windows/memory.c

PLAT_FLAGS += \
	-Wno-format

TARGET = mgba.dll

include ../base.mak
