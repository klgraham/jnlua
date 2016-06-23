# Paths
JDK_DIR=/Library/Java/JavaVirtualMachines/jdk1.8.0_66.jdk/Contents/Home/include
LUA_LIB_DIR=/Users/kgraham/Tools/torch/install/lib
LUA_INC_DIR=/Users/kgraham/Tools/torch/install/include
VERSION=5.1

# Tools
CC=gcc
LD=gcc

# Default arguments
CFLAGS=-c -fno-strict-aliasing -m64 -fPIC -O2 -Wall -DNDEBUG -D_REENTRANT -DLUA_USE_LINUX
LDFLAGS=-dynamiclib -m64

# Description blocks
all: libjnlua$(VERSION).jnilib

libjnlua$(VERSION).jnilib: jnlua.o
	$(LD) $(LDFLAGS) -o libjnlua$(VERSION).jnilib -L$(LUA_LIB_DIR) -lc -llua$(VERSION) jnlua.o

jnlua.o: ../jnlua.c
	$(CC) $(CFLAGS) -I$(JDK_DIR) -I$(LUA_INC_DIR) ../jnlua.c

clean:
	-rm libjnlua$(VERSION).jnilib jnlua.o
