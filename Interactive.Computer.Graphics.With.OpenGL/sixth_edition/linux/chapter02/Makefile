CXX = g++
CXXFLAGS = -Wall -std=c++11 -I../include -g
LDFLAGS = 
LDLIBS = -lglut -lGL -lGLU -lGLEW -lm
VPATH = ../common 

SOURCES = $(shell find ../common/ -name "*.cpp" -printf '%f\n')
HEADERS = $(shell ls ../include/*.h)
OBJECTS = $(patsubst %.cpp,%.o,$(SOURCES))

PROGRAMS_SOURCES = $(shell ls *.cpp)
PROGRAMS = $(patsubst %.cpp,%,$(PROGRAMS_SOURCES))

.PHONY: all 
all: $(PROGRAMS)

$(PROGRAMS): %: %.o $(OBJECTS)
	$(CXX) $(LDFLAGS) -o $@ $^ $(LDLIBS)

%.o: %.cpp $(HEADERS)
	$(CXX) $(CXXFLAGS) -c $< -o $@

.PHONY: clean
clean:
	rm -f *.o $(OBJECTS) $(PROGRAMS)

