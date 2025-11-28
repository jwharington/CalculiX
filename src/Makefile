
CFLAGS = -Wall -g  -I/usr/include/spooles  -DARCH="Linux" -DSPOOLES -DARPACK -DMATRIXSTORAGE -DNETWORKOUT
FFLAGS = -Wall -g -cpp

CC=cc
FC=gfortran

.c.o :
	$(CC) $(CFLAGS) -c $<
.f.o :
	$(FC) $(FFLAGS) -c $<

include Makefile.inc

SCCXMAIN = CalculiX.c

OCCXF = $(SCCXF:.f=.o)
OCCXC = $(SCCXC:.c=.o)
OCCXMAIN = $(SCCXMAIN:.c=.o)

DIR=../../SPOOLES.2.2

LIBS = -lpthread -lm -lc -lspooles -larpack -llapack -lblas -lgfortran

CalculiX: $(OCCXMAIN) CalculiX.a
	$(CC) $(CFLAGS) -c CalculiX.c; $(FC)  -Wall -g -o $@ $(OCCXMAIN) CalculiX.a $(LIBS) -fopenmp

CalculiX.a: $(OCCXF) $(OCCXC)
	ar vr $@ $?
