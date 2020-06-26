

# ar -- just archive tool, so static library is just archive of objective files
# working signature is   ar 'flags' libraryname.a  list_of_objectives.o ...
# rcs flags represents 
# r  - replace existing or insert new file(s) into the archive
# s  - act as ranlib
# c  - removing warning regarding library creation
#
#
# -L flag for gcc/g++ to specify path for static/dynamic libs
# -l flag for specifying library name such as in this make file
# -l flag examples: -lpthread -lsomeotherstaff
#  Also, there is some weird library naming convention that should be explained 

all: main.o

main.o: libmycat.a
	g++ main.cpp -c
	g++ main.o -L.  -lmycat -o final.out
libmycat.a:
	g++ lib_mylib.cpp -c 
	ar rcs $@ *.o  # $@ -- pastes name of target, in this case "libmycat.a" 
	ranlib $@ #tool that creates indexed archive to simplify linker working routine
clean:
	rm -rf *.o
	rm -rf *.a
	rm -rf *.out
