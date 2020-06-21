CC=g++
OBJ_DIRS:=main_dir/obj-main exp_dir/obj-exp kek_dir/obj-kek
#MAIN_OBJ=main_dir/obj-all
MAIN_OBJ=obj-all
INCLUDE_DIRS:=-Iexp_dir/ -Ikek_dir/  # -I flag is responsible for providing path for header files in particular object file
COMPILE_DIRS:=exp_dir kek_dir main_dir
.PHONY: all
.PHONY: clean

all: finalfile

debug: CC+=-g
debug: all

finalfile: kek.o exp.o main.o  # linking stage
	mkdir -p bin/
	mkdir -p obj-all
	for dir in $(OBJ_DIRS); do \
		cd $$dir; \
		cp *.o ./../../obj-all/; \
		cd -; \
	done
	$(CC) $(MAIN_OBJ)/*.o  -o bin/EXECUTABLE.work
main.o:
	mkdir -p main_dir/obj-main
	$(CC) $(INCLUDE_DIRS) main_dir/main.cpp -c
	mv *.o main_dir/obj-main/
exp.o:
	mkdir -p exp_dir/obj-exp
	$(CC) -c exp_dir/exp.cpp
	mv *.o exp_dir/obj-exp/
kek.o:
	mkdir -p kek_dir/obj-kek
	$(CC) -c kek_dir/kek.cpp
	mv *.o kek_dir/obj-kek/
clean:
	rm -f *.o
	rm -rf obj-*
	rm -f *.work
	rm -rf bin/
	for dir in $(COMPILE_DIRS); do rm -rf $$dir/obj-*; done
