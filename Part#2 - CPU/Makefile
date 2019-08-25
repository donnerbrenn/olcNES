B=olcCPU
O=obj
CXXFLAGS=-O3 -s -std=c++11
LDFLAGS=-pthread -lX11 -lGL -lpng -Wl,--build-id=none -Wl,--hash-style=gnu -Wl,-z,norelro -fuse-ld=gold

TARGETS=$O/olc6502.o $O/Bus.o $O/olcNes_Video1_6502.o

%/:
	mkdir -p $@

$O/%.o: %.cpp
	g++ -c -O3 -s $< -o $@

all: clean $O/ $(TARGETS)
	g++ -O3 -s $(TARGETS) $(LDFLAGS) -o $B
	wc -c $B
 
clean:
	-rm -rf $O/ $B