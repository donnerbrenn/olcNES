B=olcCPU
O=obj
CXXFLAGS=-O3 -s -std=c++11 #-flto -fno-stack-limit -ffast-math -fno-stack-protector -fno-stack-check -fno-asynchronous-unwind-tables -fno-exceptions  -funsafe-math-optimizations -fomit-frame-pointer -ffunction-sections -fdata-sections -fno-math-errno -fno-unroll-loops -fmerge-all-constants -fno-ident -mfpmath=387 -mfancy-math-387 -Bmydir -falign-functions=1 -falign-jumps=1 -falign-loops=1 -fomit-frame-pointer -fsingle-precision-constant
LDFLAGS=-pthread -lX11 -lGL -lpng -Wl,--build-id=none -Wl,--hash-style=gnu -Wl,-z,norelro -fuse-ld=gold

TARGETS=$O/olc6502.o $O/Bus.o $O/olcNes_Video1_6502.o

%/:
	mkdir -p $@

$O/%.o: %.cpp
	g++ -c -O3 -s $< -o $@

all: clean $O/ $(TARGETS)
	g++ -O3 -s $(TARGETS) $(LDFLAGS) -o $B
	# strip $B -S --strip-unneeded -R .eh_frame -R .eh_frame_hdr -R .gnu.version -R .note.ABI-tag -R .note.gnu.gold-version  -R .comment -s
	# sstrip -z $B
	# ./opt_lzma.py $B -o $B.lzma
	# cat shelldropper.sh $B.lzma > $B
	# chmod +x $B
	wc -c $B
 
clean:
	-rm -rf $O/ $B