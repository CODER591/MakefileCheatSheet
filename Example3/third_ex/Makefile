#For future repeating and education purposes:

# Creating only one makefile that will handling everything, such as creating static and shared library and their linking process, etc...
# So, Definitely for single compilation unit that worth separate Makefile(static/shared lib) it MUST be created. 
# But in my case, I want to do it in one file, for more clarity.
# Keep in mind that keep everything here is definitely is bad approach.



CC=g++

STATIC_LIB_NAME=libstaticsomefunc.a
SHARED_LIB_NAME=libsharedsomefunc.so

all: finalfile

finalfile: main.o
	$(CC) *.o -L. -lstaticsomefunc -o final.out


main.o: $(STATIC_LIB_NAME)
	$(CC) main.cpp -c

#Firstly, lets create the static library
$(STATIC_LIB_NAME):
	$(CC) stat_lib/*.cpp -c
	mv *.o stat_lib/ # definitely smells bad
	ar rcs $@ stat_lib/*.o
	#ranlib is not required, because of "s" flag


clean:
	rm -rf *.o
	rm -rf *.out
	rm -rf *.a
	rm -rf *.so
