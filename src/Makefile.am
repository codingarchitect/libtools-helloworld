AM_CPPFLAGS = -I$(srcdir)/../lib
bin_PROGRAMS = helloapp
helloapp_SOURCES = main.pc
helloapp_LDADD = ../lib/libgreeter.la
helloapp_LDADD += ../lib/libsysparams.la

CC=/usr/bin/gcc
cc=/usr/bin/gcc
# CC=/opt/oracle/developerstudio12.6/bin/cc
# cc=/opt/oracle/developerstudio12.6/bin/cc

# InstantClient Directories.
ICSDKHOME=$(ORACLE_HOME)/sdk/
ICLIBHOME=$(ORACLE_HOME)/

MKLINK=ln
REMOVE=rm -rf
CLNCACHE=cleancache
CACHEDIR=SunWS_cachea
MAKE=make
MAKEFILE=Makefile
PROCDEMO=hello-world

PROC=$(ICSDKHOME)proc
SO_EXT=.so
I_SYM=-I

CCINCLUDES= $(I_SYM). $(I_SYM)$(ICSDKHOME)include $(I_SYM)/usr/lib/gcc/x86_64-redhat-linux/4.8.5/include

# Pre-compiler Flags.
PRECOMP_INCLUDE=$(I_SYM). $(SYS_INCLUDE)
PRECOMPPUBH=$(ICSDKHOME)include
SYS_INCLUDE=sys_include=\($(PRECOMPPUBH),/usr/include,/usr/lib/gcc/x86_64-redhat-linux/4.8.5/include\)

# Compiler Flags.
OPTIMIZE=-O2
LDPATHFLAG=-L
SPFLAGS=-DLINUX -D_LARGEFILE64_SOURCE=1 -D_LARGEFILE_SOURCE=1 -DSLTS_ENABLE -DSLMXMX_ENABLE -D_REENTRANT -DNS_THREADS
CCFLAGS= -fPIC -DPRECOMP
LDFLAGS=-g
LPFLAGS=
GFLAG=
CDEBUG=
USRFLAGS=
ICLIBPATH=$(LDPATHFLAG)$(ICLIBHOME)
PFLAGS=$(CCINCLUDES) $(SPFLAGS) $(LPFLAGS)
#CFLAGS=$(GFLAG) $(OPTIMIZE) $(CDEBUG) $(CCFLAGS) $(PFLAGS) $(USRFLAGS) -H
CFLAGS=$(GFLAG) $(OPTIMIZE) $(CDEBUG) $(CCFLAGS) $(PFLAGS) $(USRFLAGS) -ansi
#CFLAGS=$(GFLAG) $(OPTIMIZE) $(CDEBUG) $(CCFLAGS) $(PFLAGS) $(USRFLAGS) -H -include "/usr/include/time.h" 


# Libraries.
PROLDLIBS=$(LDCLIENTLIBS) $(THREADLIBS)
LDCLIENTLIBS=$(ICLIBPATH) $(LLIBCLNTSH) $(LDLIBS)
LLIBCLNTSH=$(LDLIBFLAG)$(LIBCLNTSHNAME)
LDLIBFLAG=-l
LIBCLNTSHNAME=clntsh
LDLIBS=$(EXSYSLIBS) $(MATHLIB) $(USRLIBS)
EXSYSLIBS=-ldl
MATHLIB=-lm
THREADLIBS=-lpthread

C2O=$(CC) $(CFLAGS) -c $*.c
PCC2C=$(PROC) $(PROCFLAGS) iname=$(PCCSRC) $(PRECOMP_INCLUDE)
DEMO_PROC_BUILD=$(CC) -o $(EXE) $(OBJS) $(LDFLAGS) $(PROLDLIBS)

#-----------------------------------------------------------------------------
# Targets for building the proc sample programs.
# all: clean $(PROCDEMO)

$(PROCDEMO):
	$(MAKE) -f $(MAKEFILE) build OBJS=$@.o EXE=$@
	
build: $(CLNCACHE) $(OBJS)
	$(MKLINK) $(ICLIBHOME)libclntsh$(SO_EXT).11.1 $(ICLIBHOME)libclntsh$(SO_EXT)
	$(DEMO_PROC_BUILD)
	$(REMOVE) $(ICLIBHOME)libclntsh$(SO_EXT)

#-----------------------------------------------------------------------------
# Here are some rules for converting .pc -> .c -> .o
SUFFIXES: .pc .c .o

pc1:
	$(PCC2C)

.pc.c:
	$(MAKE) -f $(MAKEFILE) PROCFLAGS="$(PROCFLAGS)" PCCSRC=$* I_SYM=include= pc1

.pc.o:
	$(MAKE) -f $(MAKEFILE) PROCFLAGS="$(PROCFLAGS)" PCCSRC=$* I_SYM=include= pc1
	$(C2O)

.c.o:
	$(C2O)

#-----------------------------------------------------------------------------
# Clean up all executables, *.o and generated *.c files
clean: $(CLNCACHE)
	$(REMOVE) $(PROCDEMO) $(PROCDEMO).o $(PROCDEMO).c $(PROCDEMO).lis

cleancache:
	$(REMOVE) $(CACHEDIR)
	$(REMOVE) $(ICLIBHOME)libclntsh$(SO_EXT)

