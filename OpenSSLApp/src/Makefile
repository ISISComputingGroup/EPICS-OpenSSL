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

#===========================

include $(TOP)/configure/RULES
#----------------------------------------
#  ADD RULES AFTER THIS LINE

ifdef T_A

install:
	$(MAKE) -C $(TOP)/openssl-src -f Make.epics install T_A=$(T_A)

endif

ifeq ($(BASE_3_14),YES)
clean::
	$(MAKE) -C $(TOP)/openssl-src -f Make.epics clean
else
clean:
	$(MAKE) -C $(TOP)/openssl-src -f Make.epics clean
endif

