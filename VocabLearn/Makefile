# Makefile for VocabLearn

CXXFLAGS = -O2 $(GLOBAL_CXXFLAGS) $(DEBUGFLAGS) -fmessage-length=0 -std=c++0x
LDFLAGS = $(GLOBAL_LDFLAGS) -L../lib/ -lboost_iostreams

# Common
CXXFLAGS += -I../Common/include/
LDFLAGS += -lcommon

# KMajority
CXXFLAGS += -I../KMajorityLib/include
LDFLAGS += -lkmajority

# IncrementalKMeans
CXXFLAGS += -I../IncrementalKMeansLib/include
LDFLAGS += -lincrementalkmeans

# VocabLib
CXXFLAGS += -I../VocabLib/include
LDFLAGS += -lvocab

# OpenCV (this goes last: beware of the linking order)
CXXFLAGS += `pkg-config opencv --cflags`
LDFLAGS += `pkg-config opencv --libs`

#LDFLAGS += -Wl,-rpath=../../agast_lib/lib
#LDFLAGS += -Wl,-rpath=../../dbrief_lib/lib
#LDFLAGS += -Wl,-rpath=../lib/

SOURCES = $(wildcard *.cpp)
OBJECTS = $(SOURCES:.cpp=.o)

BIN = VocabLearn

#DEBUG = -DDEBUG
VTREEVERBOSE = -DVTREEVERBOSE

all: $(BIN)

$(BIN): $(OBJECTS)
	$(CXX) $(OBJECTS) -o $(BIN) $(LDFLAGS)

.cpp.o:
	$(CXX) $(DEBUG) $(VTREEVERBOSE) -c $(CXXFLAGS) $< -o $@

clean:
	rm -rf $(OBJECTS) $(BIN) *~
