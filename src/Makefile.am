AM_CPPFLAGS = -I$(srcdir)/../lib
bin_PROGRAMS = helloapp
helloapp_SOURCES = main.pc
helloapp_LDADD = ../lib/libgreeter.la
helloapp_LDADD += ../lib/libsysparams.la

# InstantClient Directories.
ICSDKHOME=$(ORACLE_HOME)/sdk/
ICLIBHOME=$(ORACLE_HOME)/

#-----------------------------------------------------------------------------
# Here are some rules for converting .pc -> .c -> .o
AM_CPPFLAGS += -I$(ICSDKHOME)include
AM_LDFLAGS = -L$(ICLIBHOME) -lclntsh
PROC_SYS_INCLUDE=sys_include=\($(ICSDKHOME)include,/usr/include,/usr/lib/gcc/x86_64-redhat-linux/4.8.5/include\)
PROC_INCLUDE=INCLUDE=\(../lib\)
.pc.c:
	$(ICSDKHOME)proc lines=yes iname=$< $(PROC_SYS_INCLUDE) $(PROC_INCLUDE)

