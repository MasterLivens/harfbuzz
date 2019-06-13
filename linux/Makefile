


COMPILE = arm-none-linux-gnueabi-
#COMPILE = /root/work/licheepi/DIY/buildroot-2017.02.7/output/host/usr/bin/arm-linux-gnueabihf-
#COMPILE = /usr/local/arm/4.2.2-eabi/usr/bin/arm-unknown-linux-gnueabi-
CC     	= $(COMPILE)gcc
CXX    	= $(COMPILE)g++ 
AR     	= $(COMPILE)ar
LD     	= $(COMPILE)ld
OBJCOPY	= $(COMPILE)objcopy
NM      = $(COMPILE)nm
OBJDUMP	= $(COMPILE)objdump
CHMOD  	= chmod
PWD     = $(shell pwd)



CFLAGS += -fPIC -O2
CFLAGS += -DHB_NO_MT -DHAVE_OT 

# hardware float
#CFLAGS += --sysroot=/root/work/licheepi/DIY/buildroot-2017.02.7/output/host/usr/arm-buildroot-linux-gnueabihf/sysroot
#CFLAGS += -I/root/work/licheepi/DIY/buildroot-2017.02.7/output/host/usr/arm-buildroot-linux-gnueabihf/sysroot/usr/include/glib-2.0
#CFLAGS += -I/root/work/licheepi/DIY/buildroot-2017.02.7/output/host/usr/arm-buildroot-linux-gnueabihf/sysroot/usr/lib/glib-2.0/include/

# software float
#CFLAGS += --sysroot=/root/work/sinlinx/a33/lichee/out/sun8iw5p1/linux/common/buildroot/host/usr/arm-unknown-linux-gnueabi/sysroot

CFLAGS += -I../src/hb-ucdn
CFLAGS += -I../deps/include

CPPFLAGS += -Wall -DNDEBUG $(CFLAGS) 

LDFLAGS += -shared 



HARFBUZZ_SOURCE = \
	../src/hb-blob.cc \
	../src/hb-buffer-serialize.cc \
	../src/hb-buffer.cc \
	../src/hb-common.cc \
	../src/hb-fallback-shape.cc \
	../src/hb-face.cc \
	../src/hb-font.cc \
	../src/hb-ot-tag.cc \
	../src/hb-set.cc \
	../src/hb-shape.cc \
	../src/hb-shape-plan.cc \
	../src/hb-shaper.cc \
	../src/hb-ft.cc \
	../src/hb-tt-font.cc \
	../src/hb-unicode.cc \
	../src/hb-warning.cc \
	../src/hb-ot-layout.cc \
	../src/hb-ot-map.cc \
	../src/hb-ot-shape.cc \
	../src/hb-ot-shape-complex-arabic.cc \
	../src/hb-ot-shape-complex-default.cc \
	../src/hb-ot-shape-complex-indic.cc \
	../src/hb-ot-shape-complex-indic-table.cc \
	../src/hb-ot-shape-complex-myanmar.cc \
	../src/hb-ot-shape-complex-sea.cc \
	../src/hb-ot-shape-complex-thai.cc \
	../src/hb-ot-shape-normalize.cc \
	../src/hb-ot-shape-fallback.cc \
	../src/hb-ucdn.cc \
	../src/hb-ucdn/ucdn.c

.o.cc:
	$(CXX) $(CFLAGS) $< -c $@

HARFBUZZ_OBJS += $(addsuffix .o, $(basename $(HARFBUZZ_SOURCE)))

all : libharfbuzz 

libharfbuzz : ${HARFBUZZ_OBJS}
	$(CXX) ${LDFLAGS} ${HARFBUZZ_OBJS} -o $@.so
	$(AR) -r  $@.a ${HARFBUZZ_OBJS} 
	

clean:
	rm -rf $(HARFBUZZ_OBJS) 
	rm -rf libharfbuzz.so

