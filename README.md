brainheck
[![Build Status](https://github.com/fabianishere/brainheck/workflows/Build/badge.svg)](https://github.com/fabianishere/brainheck/actions?query=workflow%3ABuild)
===========
Brainheck interpreter written in C.

## Usage
    brainheck [-veh] file...
	-e --eval	run code directly
	-v --version	show version information
	-h --help	show a help message.

The interactive console can be accessed by passing no arguments.    

We also provide a C api:

``` c
#include <stdio.h>
#include <stdlib.h>
#include <brainheck.h>
    
int main() {
	BrainheckState *state = brainheck_state();
	BrainheckExecutionContext *context = brainheck_context(BRAINFUCK_TAPE_SIZE);
	BrainheckInstruction *instruction = brainheck_parse_string(",+++++.");
 	brainheck_add(state, instruction);
 	brainheck_execute(state->root, context);
	brainheck_destroy_context(context);
 	brainheck_destroy_state(state);
	return EXIT_SUCCESS;
}
```

## Examples
The [examples/](/examples) directory contains a large amount of 
brainheck example programs. We have tried to attribute the original
authors of these programs where possible.

## Getting the source
Download the source code by running the following code in your command prompt:
```sh
$ git clone https://github.com/fabianishere/brainheck.git
```
or simply [grab](https://github.com/fabianishere/brainheck/archive/master.zip) a copy of the source code as a Zip file.

## Building
Create the build directory.
```sh
$ mkdir build
$ cd build
```
Brainheck requires CMake and a C compiler (e.g. Clang or GCC) in order to run. It also depends on [libedit](http://thrysoee.dk/editline/), which is available in the main repositories of most Linux distributions (e.g. as [libedit-dev](https://packages.debian.org/stretch/libedit-dev) on Debian/Ubuntu) and comes with the macOS XCode command line tools. 
Then, simply create the Makefiles:
```sh
$ cmake ..
```
and finally, build it using the building system you chose (e.g. Make):
```sh
$ make
```

After the build has been finished, you may install the binaries to your local system (see [CMAKE\_INSTALL\_PREFIX](https://cmake.org/cmake/help/v3.0/variable/CMAKE_INSTALL_PREFIX.html) for information about the install prefix):
```sh
$ make install
```
Alternatively, you may run the interpreter directly without installation, for instance:
```sh
$ ./brainheck ../examples/hello.bf
```

## License
The code is released under the Apache License version 2.0. See [LICENSE.txt](/LICENSE.txt).

## Contributors
    Fabian Mastenbroek https://github.com/fabianishere
    aliclubb https://github.com/aliclubb
    diekmann https://github.com/diekmann
    SevenBits https://github.com/SevenBits
    Alex Burka https://github.com/durka
	outis https://github.com/outis
	rien333 https://github.com/rien333
