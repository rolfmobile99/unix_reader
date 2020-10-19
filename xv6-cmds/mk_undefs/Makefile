#
# generate a list of "Undefined references" for a list of program sources
#   located in the directory above.
# the sources should be organized as one file per program.
#
# -rolf (oct 2020)

CFLAGS=
CC=cc

SRC_PATH=..
FILES = cat.c echo.c grep.c kill.c ln.c ls.c mkdir.c mkfs.c rm.c sh.c wc.c

TARGET=sorted.undef


SOURCES = $(FILES:%.c=$(SRC_PATH)/%.c)
OBJECTS = $(SOURCES:%.c=%.o)


%.o : %.c
	$(CC) -c $(CFLAGS) -o $@ $<


.PHONY: all clean

all: $(OBJECTS)

sorted.undef: $(OBJECTS)
	nm $(OBJECTS) | egrep '\s+U\s' > tmp.undef
	sort --unique tmp.undef > sorted.undef

wc:
	wc -l $(SOURCES)

echo:
	echo $(OBJECTS)

clean: 
	/bin/rm $(OBJECTS) tmp.undef

