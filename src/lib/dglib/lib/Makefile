LIB = dglib.a 
SRCS = $(wildcard *.cpp) 
OBJS = $(SRCS:.cpp=.o)
DEPS = $(SRCS:.cpp=.depends)
include ../../../MakeIncludes
SHAPELIBDIR = ../../shapelib
PROJ4LIBDIR = ../../proj4lib
INCDIRS = -I../include -I$(SHAPELIBDIR)/include -I$(GDAL_HDR_DIR) -I$(PROJ4LIBDIR)/include
CCFLAGS = ${INCDIRS} ${ADD_CPP_FLAGS} 

.PHONY: clean all

all: $(LIB)

$(LIB): $(SRC) $(OBJS) $(DEPS)
	ar ruv $(LIB) $(OBJS)
	ranlib $(LIB)

%.o: %.cpp 
	$(CPPCOMP) -c $< $(CCFLAGS)

%.depends: %.cpp
	$(CPPCOMP) -M $(CCFLAGS) $< > $@

clean:
	rm -rf $(OBJS) $(LIB) $(DEPS) ii_files ti_files make.out

-include $(DEPS)
