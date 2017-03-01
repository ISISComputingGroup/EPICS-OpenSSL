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
	$(PERL) $(TOP)/openssl-src/Configure $(OPENSSL_ARCH) no-asm zlib --prefix=$(abspath $(TOP)/install/$(T_A)) --openssldir=$(abspath $(TOP)/install/conf) --with-zlib-include=$(ZLIB)/include --with-zlib-lib=$(ZLIB)/lib/$(T_A)/zlib.lib
	nmake
	nmake install
	-$(MKDIR) $(TOP)/bin
	-$(MKDIR) $(TOP)/bin/$(T_A)
	-$(MKDIR) $(TOP)/lib
	-$(MKDIR) $(TOP)/lib/$(T_A)
	-$(MKDIR) $(TOP)/include
	-$(MKDIR) $(TOP)/include/openssl
	$(CP) -f $(TOP)/install/$(T_A)/include/openssl/*.h* $(TOP)/include/openssl/
	$(CP) -f $(TOP)/install/$(T_A)/lib/*.lib $(TOP)/lib/$(T_A)/
	$(CP) -f $(TOP)/install/$(T_A)/bin/* $(TOP)/bin/$(T_A)/
endif
endif

