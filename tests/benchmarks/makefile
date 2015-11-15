CPPSRCS		= ssalloc.cc test_demo.cc
TARGET		= test_cuckoo

    
ROOT 		?= .
LIBSSMEM := $(ROOT)/external

CPP			= g++_mic

CPPFLAGS	=-std=c++0x -O3 -m64 -Wall -DTAS -DGC=1 -fno-strict-aliasing -DCORE_NUM=32 -DFREQ_GHZ=1.801 -DNDEBUG -DINTEL64 -D_REENTRANT  -DDO_TIMINGS -DLATENCY_ALL_CORES=0  -lrt -pthread -I$(ROOT) -I$(LIBSSMEM)/include# -DUSE_SSPFD -DCOMPUTE_LATENCY
LFLAGS		=-std=c++0x -O3 -m64 -Wall -DTAS -DGC=1 -fno-strict-aliasing -DCORE_NUM=32 -DFREQ_GHZ=1.801 -DNDEBUG -DINTEL64 -D_REENTRANT  -DDO_TIMINGS -DLATENCY_ALL_CORES=0  -lrt -pthread -I$(ROOT) #-DUSE_SSPFD -L$(LIBSSMEM)/lib -lsspfd -lsspfd_x86_64 -lssmem_x86_64 -DCOMPUTE_LATENCY

OBJS		= $(CPPSRCS:.cpp=.o)

all: $(TARGET)

test_demo.o:
	$(CPP) $(CPPFLAGS) -c ./tests/benchmarks/test_demo.cc 
ssalloc.o:
	$(CPP) $(CPPFLAGS) -c ./tests/benchmarks/ssalloc.cc 
cpp_framework.o:
	$(CPP) $(CPPFLAGS) -c ./framework/cpp_framework.cpp

$(TARGET): $(OBJS)
	$(CPP) $(LFLAGS) $(OBJS) -o $(TARGET) $(LFLAGS)

clean:
	rm -f test_demo.o ssalloc.o $(TARGET) 

depend:
	mkdep $(SRCS)
