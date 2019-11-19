

CC=gcc

CFLAGS = -m32 -Ilibmylcd/include/ -I../../include/  -Wall -O3 -fomit-frame-pointer -D_WIN32 -D_M_IX86 -mwin32 -D_WIN32_WINNT=0x0500 -DWINVER=0x0500 -D__WIN32__=1 -std=gnu99 -funroll-loops -finline-functions -pipe
LIBS = -m32 -Llibmylcd/libs/ -L../../libs/ -L"lib" 
  

EXAMPLES=irc.exe

all : $(EXAMPLES)


%.exe: %.o
	$(CC) $(LIBS) -o $@ $^ -lm -lmylcddll -liphlpapi -lwininet -lwsock32 -lgdi32 -lws2_32 -lpthread -lwinmm -lpsapi -lhid -lsetupapi -lcomctl32 -loleaut32  -lole32 -luuid
	strip.exe $@
	copy $@ "../build/$@"
	del -f $@

%.o: %.c $(DEPS)
	$(CC) -c -o $@ $< $(CFLAGS)


irc.exe: lock.o network.o net.o send.o bot.o g15.o config.o irc.o


clean :
	rm -f *.exe *.o *.bak
	rm -f usbd480_plugin.dll



### PHONY define
.PHONY: all all-before all-after clean clean-custom



