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

LDFLAGS_64 =
LDFLAGS = -shared $(LDFLAGS_$(ARCH)) $(CCFLAGS)

DEST_64 = ../../../../../output/dll

PLAT_SRCS += \
	$(ROOT_DIR)/platform/posix/memory.c

PLAT_FLAGS += \
	-DHAVE_LOCALE -fvisibility=hidden

TARGET = libmgba.dll.so

include ../base.mak
