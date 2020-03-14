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

all:  exp.o main.o
	mkdir -p obj-all   # mkdir -p would not brake makefile if folder exist
	for dir in $(DIRS); do \
		cd $$dir; \
		cp *.o ./../obj-all; \
		cd -; \
	done
#	$(CC) $(wildcard ./obj-all/*.o) -o EXECUTABLE.work
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
