
CC = g++ -O3 -fPIC -MMD

CFLAGS		= -I. -I..

LDFLAGS		= -L. -L..

.SUFFIXES: .cpp

SRCS		= RAPID.cpp build.cpp collide.cpp overlap.cpp

OBJECTS		= RAPID.o build.o collide.o overlap.o 

CLEAN		= $(OBJECTS) *.a *.o *~ Dependencies

default: library

install: libRAPID.a
library: libRAPID.a

libRAPID.a: $(OBJECTS)
	/bin/rm -f libRAPID.a
	ar ruv libRAPID.a $(OBJECTS)

.C.o:
	$(CC) $(CFLAGS) -c $< -o $@
	cat $*.d >> Dependencies
	rm -rf $*.d

.cpp.o:
	$(CC) $(CFLAGS) -c $< -o $@
	cat $*.d >> Dependencies
	rm -rf $*.d

Dependencies:
	touch Dependencies

clean:
	touch clean.a
	/bin/rm -f $(CLEAN)

-include Dependencies
