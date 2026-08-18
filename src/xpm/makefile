#
# XPM makefile for HP-UX 11i v3 PA-RISC.
#
# Built with the HP ANSI C compiler in /opt/ansic/bin in -Ae mode against the
# system X11R6 headers in /usr/include/X11.  HP-UX is SysV, so -DSYSV picks
# string.h plus the bcopy/bzero macros in XpmI.h.
#

CC = /opt/ansic/bin/cc
AR = ar r
RM = rm -f
LN = ln -s

XINCLUDE = /usr/include

CDEBUGFLAGS = -Ae -O
DEFINES = -DZPIPE -DSYSV

CFLAGS = $(CDEBUGFLAGS) $(DEFINES) -I. -I$(XINCLUDE)

OBJS= data.o create.o misc.o rgb.o scan.o parse.o hashtab.o \
      WrFFrP.o RdFToP.o CrPFrDat.o CrDatFrP.o \
      WrFFrI.o RdFToI.o CrIFrDat.o CrDatFrI.o \
      CrIFrBuf.o CrPFrBuf.o CrBufFrI.o CrBufFrP.o \
      RdFToDat.o WrFFrDat.o \
      Attrib.o CrIFrP.o CrPFrI.o Image.o Info.o RdFToBuf.o WrFFrBuf.o

all: ../X11/xpm.h libXpm.a

libXpm.a: $(OBJS)
	$(RM) libXpm.a
	$(AR) libXpm.a $(OBJS)

# sim includes <X11/xpm.h>, so expose this xpm.h under an X11 directory.
../X11/xpm.h: xpm.h
	@if [ -d ../X11 ]; then set +x; else (set -x; mkdir ../X11); fi
	$(RM) ../X11/xpm.h
	$(LN) ../xpm/xpm.h ../X11/xpm.h

clean:
	$(RM) *.o libXpm.a ../X11/xpm.h

$(OBJS): XpmI.h xpm.h
