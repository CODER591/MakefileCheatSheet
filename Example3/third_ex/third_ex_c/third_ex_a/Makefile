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
	$(CC) *.o  ./$(SHARED_LIB_NAME) -o final.out


main.o: $(SHARED_LIB_NAME)
	$(CC) main.cpp -c


#Secondly, lets build the shared library.
$(SHARED_LIB_NAME): $(STATIC_LIB_NAME)
	$(CC) -fPIC -shared -I./stat_lib/ shar_lib/first_shar.cpp -L. -lstaticsomefunc  -o $@


# Firstly, lets create the static library
# There is one thing, with "-fPIC", this flag is required in case we are linking static library into the shared library
# For details look into the "Static Libraries Issues on 64-bit Linux" chapter of "Advanced C and C++ Compiling" book

$(STATIC_LIB_NAME):
	$(CC) stat_lib/*.cpp -fPIC -c
	mv *.o stat_lib/ # definitely smells bad
	ar rcs $@ stat_lib/*.o
	#ranlib is not required, because of "s" flag


clean:
	rm -rf *.o
	rm -rf *.out
	rm -rf *.a
	rm -rf *.so
