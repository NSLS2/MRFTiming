TOP=../..

include $(TOP)/configure/CONFIG
#----------------------------------------
#  ADD MACRO DEFINITIONS BELOW HERE

# Use typed rset structure (see 3.16.1 release notes)
USR_CPPFLAGS += -DUSE_TYPED_RSET

# Build the IOC application
PROD_IOC = MRFTiming

# MRFTiming.dbd will be created and installed
DBD += MRFTiming.dbd

# MRFTiming.dbd will include these files:
MRFTiming_DBD += base.dbd
# based on the instruction 'Using the device support'
MRFTiming_DBD += mrfUdpIp.dbd
# for supplemental database files
MRFTiming_DBD += busySupport.dbd
MRFTiming_DBD += calcSupport.dbd
# NSLS-II standard moduels
MRFTiming_DBD += asSupport.dbd
MRFTiming_DBD += devIocStats.dbd
MRFTiming_DBD += caPutLog.dbd
MRFTiming_DBD += reccaster.dbd

# MRFTiming_registerRecordDeviceDriver.cpp derives from MRFTiming.dbd
MRFTiming_SRCS += MRFTiming_registerRecordDeviceDriver.cpp

# Build the main IOC entry point where needed
MRFTiming_SRCS_DEFAULT += MRFTimingMain.cpp
MRFTiming_SRCS_vxWorks += -nil-

# Link in the code from our support library
# based on the instruction 'Using the device support'
MRFTiming_LIBS += mrfCommon
MRFTiming_LIBS += mrfEpics
MRFTiming_LIBS += mrfEpicsUdpIp
MRFTiming_LIBS += mrfUdpIp
# for supplemental database files
MRFTiming_LIBS += busy
MRFTiming_LIBS += calc
# NSLS-II standard moduels
MRFTiming_LIBS += autosave
MRFTiming_LIBS += devIocStats
MRFTiming_LIBS += caPutLog
MRFTiming_LIBS += reccaster

# Link QSRV (pvAccess Server) if available
ifdef EPICS_QSRV_MAJOR_VERSION
    MRFTiming_LIBS += qsrv
    MRFTiming_LIBS += $(EPICS_BASE_PVA_CORE_LIBS)
    MRFTiming_DBD += PVAServerRegister.dbd
    MRFTiming_DBD += qsrv.dbd
endif

# Finally link IOC to the EPICS Base libraries
MRFTiming_LIBS += $(EPICS_BASE_IOC_LIBS)

include $(TOP)/configure/RULES
#----------------------------------------
#  ADD EXTRA GNUMAKE RULES BELOW HERE
