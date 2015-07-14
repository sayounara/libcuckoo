CPPSRCS		= ssalloc.cc test_demo.cc
TARGET		= test_cuckoo

    
ROOT 		?= .
LIBSSMEM := $(ROOT)/external

CPP			= g++

CPPFLAGS	=-std=c++11 -O3 -m64 -DNDEBUG -DINTEL64 -D_REENTRANT -lrt -pthread -I$(ROOT)/include -I$(LIBSSMEM)/include
LFLAGS		=-std=c++11 -O3 -m64 -DNDEBUG -DINTEL64 -D_REENTRANT -lrt -pthread -I$(ROOT)/include -L$(LIBSSMEM)/lib -lsspfd_x86_64 -lssmem_x86_64

OBJS		= $(CPPSRCS:.cpp=.o)

all: $(TARGET)

test_demo.o:
	$(CPP) $(CPPFLAGS) -c ./tests/benchmarks/test_demo.cc -g
ssalloc.o:
	$(CPP) $(CPPFLAGS) -c ./tests/benchmarks/ssalloc.cc -g
#cpp_framework.o:
#	$(CPP) $(CPPFLAGS) -c ./framework/cpp_framework.cpp -g

$(TARGET): $(OBJS)
	$(CPP) $(LFLAGS) $(OBJS) -o $(TARGET) -g

clean:
	rm -f test_demo.o ssalloc.o $(TARGET)

depend:
	mkdep $(SRCS)
