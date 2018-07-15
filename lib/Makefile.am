lib_LTLIBRARIES = libgreeter.la libsysparams.la
libgreeter_la_SOURCES = morning-greeter.c morning-greeter.h
libgreeter_la_SOURCES += afternoon-greeter.c afternoon-greeter.h
libgreeter_la_SOURCES += evening-greeter.c evening-greeter.h
libgreeter_la_SOURCES += night-greeter.c night-greeter.h
libsysparams_la_SOURCES = sys-params.pc sys-params.h

# InstantClient Directories.
ICSDKHOME=$(ORACLE_HOME)/sdk/
ICLIBHOME=$(ORACLE_HOME)/

#-----------------------------------------------------------------------------
# Here are some rules for converting .pc -> .c -> .o
AM_CPPFLAGS = -I$(ICSDKHOME)include
AM_LDFLAGS = -L$(ICLIBHOME) -lclntsh
SYS_INCLUDE=sys_include=\($(ICSDKHOME)include,/usr/include,/usr/lib/gcc/x86_64-redhat-linux/4.8.5/include\)
.pc.c:
	$(ICSDKHOME)proc lines=yes iname=$< $(SYS_INCLUDE)
