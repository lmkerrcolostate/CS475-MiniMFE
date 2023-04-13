CFLAGS= -O3  -std=c99  -I/usr/include/malloc/
LIBRARIES=-lm
CC?=gcc
OBJS = MiniMFE.o external_functions.o
all: plain check verify verify-rand

debug: CFLAGS =-DDEBUG -g -Wall -Wextra -std=c99 -I/usr/include/malloc/
debug: all
		
plain: $(OBJS)
	$(CC) MiniMFE-wrapper.c -o MiniMFE $(OBJS) $(CFLAGS) $(LIBRARIES)

check: $(OBJS)
	$(CC) MiniMFE-wrapper.c -o MiniMFE.check $(OBJS) $(CFLAGS) $(LIBRARIES) -DCHECKING

verify: $(OBJS) MiniMFE_verify.o
	$(CC) MiniMFE-wrapper.c -o MiniMFE.verify $(OBJS) MiniMFE_verify.o $(CFLAGS) $(LIBRARIES) -DVERIFY

verify-rand: $(OBJS) MiniMFE_verify.o
	$(CC) MiniMFE-wrapper.c -o MiniMFE.verify-rand $(OBJS) MiniMFE_verify.o $(CFLAGS) $(LIBRARIES) -DVERIFY -DRANDOM

MiniMFE.o : MiniMFE.c
	$(CC) MiniMFE.c -o MiniMFE.o $(CFLAGS) $(LIBRARIES) -c

MiniMFE_verify.o : MiniMFE_verify.c
	$(CC) MiniMFE_verify.c -o MiniMFE_verify.o $(CFLAGS) $(LIBRARIES) -c

external_functions.o: external_functions.c
	$(CC) external_functions.c -o external_functions.o $(CFLAGS) $(LIBRARIES) -c

tar: MiniMFE.c MiniMFE-wrapper.c MiniMFE_verify.c external_functions.h external_functions.c Makefile
	tar -cvf MiniMFE.tar $^

clean:
	rm -f *.o MiniMFE MiniMFE.check MiniMFE.verify MiniMFE.verify-rand
