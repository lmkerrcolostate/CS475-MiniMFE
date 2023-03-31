CFLAGS= -O3  -std=c99  -I/usr/include/malloc/
LIBRARIES=-lm
CC?=gcc
OBJS = ToyMFE.o 
all: plain check

debug: CFLAGS =-DDEBUG -g -Wall -Wextra -std=c99 -I/usr/include/malloc/
debug: all
		
plain: $(OBJS)
	$(CC) ToyMFE-wrapper.c -o ToyMFE $(OBJS) $(CFLAGS) $(LIBRARIES)

check: $(OBJS)
	$(CC) ToyMFE-wrapper.c -o ToyMFE.check $(OBJS) $(CFLAGS) $(LIBRARIES) -DCHECKING

verify: $(OBJS) ToyMFE_verify.o
	$(CC) ToyMFE-wrapper.c -o ToyMFE.verify $(OBJS) ToyMFE_verify.o $(CFLAGS) $(LIBRARIES) -DVERIFY

verify-rand: $(OBJS) ToyMFE_verify.o
	$(CC) ToyMFE-wrapper.c -o ToyMFE.verify-rand $(OBJS) ToyMFE_verify.o $(CFLAGS) $(LIBRARIES) -DVERIFY -DRANDOM

ToyMFE.o : ToyMFE.c
	$(CC) ToyMFE.c -o ToyMFE.o $(CFLAGS) $(LIBRARIES) -c

ToyMFE_verify.o : ToyMFE_verify.c
	$(CC) ToyMFE_verify.c -o ToyMFE_verify.o $(CFLAGS) $(LIBRARIES) -c

clean:
	rm -f *.o ToyMFE ToyMFE.check ToyMFE.verify ToyMFE.verify-rand
