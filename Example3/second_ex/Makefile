
#This example demonstrates how to build and link shared(dynamic) library to executable
# TODO: describe here naming convention
# Compile flags explanation:
# -Wall   -- simply show all noticed warnings
# -fPIC   -- PIC stands for (Position Independent Code)   this flag allows the following code to be referenced at any virtual address at runtime

#Also, I should take a look into "Advanced C and C++ compiling" book


SHAR_LIB_NAME=libmylibrary.so

all: main.o
	g++ -Wall main.o ./$(SHAR_LIB_NAME)  -o final.out  ## funny thing, I was not able to properly link  the program without "./" before "$(SHAR_LIB_NAME)"

main.o: $(SHAR_LIB_NAME)
	g++ main.cpp -c

$(SHAR_LIB_NAME):
	g++ -fPIC -shared sharlib/kekshlib.cpp -o $@

clean:
	rm -rf *.so
	rm -rf *.o
	rm -rf *.out

