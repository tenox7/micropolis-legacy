#
# XPM makefile for Solaris 2.5.1 PowerPC.
#
# Built with GCC 2.95.3 from /usr/local/bin against the OpenWindows 3.5.1
# X11R5 headers in /usr/openwin/include. -DSVR4 picks string.h plus the
# bcopy/bzero macros in XpmI.h.
#

CC = gcc
AR = ar r
RM = rm -f
LN = ln -s

XINCLUDE = /usr/openwin/include

CDEBUGFLAGS = -O
DEFINES = -DZPIPE -DSVR4

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
