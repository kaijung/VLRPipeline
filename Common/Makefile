# Makefile for Common

CXXFLAGS = -O2 $(GLOBAL_CXXFLAGS) $(DEBUGFLAGS) -fmessage-length=0 -std=c++11 -fpic -I./include/ 
LDFLAGS = $(GLOBAL_LDFLAGS) -lboost_iostreams -lmemcached

# OpenCV (this goes last: beware of the linking order)
CXXFLAGS += `pkg-config opencv --cflags`
LDFLAGS += `pkg-config opencv --libs`

SOURCES = $(wildcard src/*.cpp)
OBJECTS = $(SOURCES:.cpp=.o)

BINLIB=../lib

LIB = libcommon

#FILEUTILSVERBOSE = -DFILEUTILSVERBOSE
#DYNMATVERBOSE = -DDYNMATVERBOSE
#MAXCACHESIZE = -DMAX_CACHE_SIZE=1200000000

all: $(LIB).so

$(LIB).so: $(OBJECTS)
	mkdir -p $(BINLIB)
	$(CXX) -shared $(OBJECTS) -o $(BINLIB)/$@ $(LDFLAGS)

.cpp.o:
	$(CXX) $(FILEUTILSVERBOSE) $(DYNMATVERBOSE) $(MAXCACHESIZE) -c $(CXXFLAGS) $< -o $@

clean:
	rm -f $(OBJECTS) $(BINLIB)/$(LIB) *~
