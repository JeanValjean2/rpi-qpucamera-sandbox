CC	=	gcc
CFLAGS	= -std=gnu99 -g
LDFLAGS	=

all: simple

INCLUDES	=	-I./\
				-I/opt/vc/include/\
				-I/opt/vc/src/hello_pi/hello_fft

SOURCES	=	/opt/vc/src/hello_pi/hello_fft/mailbox.c qpu.c

LDFLAGS	=	-L/opt/vc/lib/ -lbcm_host -ldl

simple: clean asm
	$(CC) $(INCLUDES) $(SOURCES) $(CFLAGS) $(LDFLAGS) simple.c -o $@

asm: simple.asm helloworld.asm
	vc4asm -V -o simple.bin simple.asm vc4.qinc
	vc4asm -V -o helloworld.bin helloworld.asm vc4.qinc

clean:
	rm -f simple
	rm -f simple.bin
	rm -f helloworld.bin 
