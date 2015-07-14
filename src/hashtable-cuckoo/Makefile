ROOT = ../..

include $(ROOT)/common/Makefile.common

BINS  = $(BINDIR)/lb-ht_cuckoo
PROF = $(ROOT)/src

CC = g++
LDFLAGS += -std=c++11  -L$(CUCKOO_LIBS) -lcityhash 
TEST_FILE = test_simple.cc

.PHONY:	all clean

all:	main

measurements.o:
	$(CC) $(CFLAGS) -c -o $(BUILDIR)/measurements.o $(PROF)/measurements.c

ssalloc.o:
	$(CC) $(CFLAGS) -c -o $(BUILDIR)/ssalloc.o $(PROF)/ssalloc.c

test.o: $(TEST_FILE)
	$(CC) $(CFLAGS) -c -o $(BUILDIR)/test.o $(TEST_FILE) -I$(CUCKOO_INCLUDES)

main: 	test.o ssalloc.o measurements.o
	$(CC) $(CFLAGS) $(BUILDIR)/ssalloc.o $(BUILDIR)/measurements.o $(BUILDIR)/test.o -o $(BINS) $(LDFLAGS) 

clean:
	rm -f $(BINS)
