CC=g++
OBJ_DIRS:=obj-main obj-exp
MAIN_OBJ=obj-all
INCLUDE_DIRS:=-Iexp_dir/

.PHONY: all
.PHONY: clean

all: finalfile

debug: CC+=-g
debug: all

finalfile:  exp.o main.o  ## linking stage
	mkdir -p obj-all
	for dir in $(OBJ_DIRS); do \
		cd $$dir; \
		cp *.o ./../obj-all; \
		cd -; \
	done
	$(CC)  $(MAIN_OBJ)/*.o  -o EXECUTABLE.work
main.o:
	mkdir -p obj-main
	$(CC) $(INCLUDE_DIRS) main.cpp -c
	mv *.o obj-main/
exp.o:
	mkdir -p obj-exp
	$(CC) -c exp_dir/exp.cpp
	mv *.o obj-exp/
clean:
	rm -f *.o
	rm -rf obj-*
	rm -f *.work
