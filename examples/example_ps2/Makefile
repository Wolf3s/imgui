DEBUG=1

EE_BIN = ps2_imgui_sample.elf
EE_OBJS = main.o gfx.o pad.o \
		  drawing/drawing.o drawing/drawing_controller.o \
		  widgets/widget_cursor.o widgets/widget_gamepad.o widgets/widget_icon.o widgets/widget_misc.o
EE_LIBS += -lpad

# Add imgui references
EE_OBJS += ../../imgui.o ../../imgui_demo.o ../../imgui_draw.o ../../imgui_tables.o ../../imgui_widgets.o
EE_OBJS += ../../backends/imgui_impl_ps2sdk.o ../../backends/imgui_impl_ps2gskit.o
EE_INCS += -I../.. -I../../backends
EE_CXXFLAGS += -std=c++14

# Add gsKit references
EE_INCS += -I$(GSKIT)/include
EE_LIBS += -lgskit_toolkit -lgskit -ldmakit
EE_LDFLAGS += -L$(GSKIT)/lib

ifeq ($(DEBUG),1)
EE_CXXFLAGS += -DDEBUG -g
EE_LDFLAGS += -g
else
EE_LDFLAGS += -s
endif

all: $(EE_BIN)

clean:
	rm -f $(EE_BIN) $(EE_OBJS)

run: $(EE_BIN)
	ps2client -h 192.168.0.85 execee host:$(EE_BIN)

reset:
	ps2client reset

include $(PS2SDK)/Defs.make
include $(PS2SDK)/samples/Makefile.pref
include $(PS2SDK)/samples/Makefile.eeglobal_cpp
