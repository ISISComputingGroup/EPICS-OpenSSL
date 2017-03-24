TOP=../..

include $(TOP)/configure/CONFIG
#----------------------------------------
#  ADD MACRO DEFINITIONS AFTER THIS LINE
#=============================

#==================================================
# build a support library

LIBRARY_IOC += OpenSSL

# xxxRecord.h will be created from xxxRecord.dbd
#DBDINC += xxxRecord
# install OpenSSL.dbd into <top>/dbd
DBD += OpenSSL.dbd

# specify all source files to be compiled and added to the library
#OpenSSL_SRCS += xxx

OpenSSL_LIBS += $(EPICS_BASE_IOC_LIBS)

# remove EPICS default of -w which nmake does not like
override MAKEFLAGS=

ifneq ($(findstring win32-x86,$(EPICS_HOST_ARCH)),)
OPENSSL_ARCH=VC-WIN32
else
OPENSSL_ARCH=VC-WIN64A
endif
#===========================

include $(TOP)/configure/RULES
#----------------------------------------
#  ADD RULES AFTER THIS LINE

# linux-elf --debug --release no-shared
#	--with-zlib-include
#	--with-zlib-lib
ifdef T_A
ifeq ($(OS_CLASS),WIN32)
install:
	$(MAKE) -C $(TOP)/openssl-src -f Makefile.epics install T_A=$(T_A) OPENSSL_ARCH=$(OPENSSL_ARCH) ZLIB=$(ZLIB)

endif
endif