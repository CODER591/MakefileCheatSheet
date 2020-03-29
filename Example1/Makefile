CC=g++  #just variable same as in bash

#VAR1 = recursively expanded variable
#VAR2 := single expanded variable (as usual variable)

DIRS:=obj-main obj-exp
MAIN_OBJ=obj-all

# $ -make variable dereferencing
# $$ -shell var dereferencing

# .PHONY meaning:
# All "phoned" targets are threated only as targets, not files

.PHONY: all
.PHONY: clean

all: finalfile

# Also comment regarding -g flag
# It needs to be used even linking, not only when creating "final" objective
# So, lets add this globally
debug: CC+=-g # Now we can build debug version too
debug: all

finalfile:  exp.o main.o
	mkdir -p obj-all   # mkdir -p would not brake makefile if folder exist
	for dir in $(DIRS); do \
		cd $$dir; \
		cp *.o ./../obj-all; \
		cd -; \
	done
#	$(CC) $(wildcard ./obj-all/*.o) -o EXECUTABLE.work  #bad example with wildcard, it would not work
	$(CC) $(MAIN_OBJ)/*.o  -o EXECUTABLE.work
main.o:
	mkdir -p obj-main
	$(CC) main.cpp -c
	mv *.o obj-main/
exp.o:
	mkdir -p obj-exp
	$(CC) -c exp.cpp
	mv *.o obj-exp/
clean:
	rm -f *.o
	rm -rf obj-*
	rm -f *.work
