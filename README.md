# libdeep: C/C++ library for deep learning

<img src="https://github.com/bashrc/libdeep/blob/master/img/logo.png?raw=true" width=200/>

This is a C library which can be used in deep learning applications.  It allows multiple layers to be trained and also includes the dropouts technique to avoid overfitting the data. What differentiates libdeep from the numerous other deep learning systems out there is that it's relatively small and that trained networks can be exported as *completely standalone C or Python programs* which can either be used via the commandline or within and Arduino IDE for creating robotics or IoT applications.

A Python API for libdeep can be found at https://github.com/bashrc/libdeep-python

<img src="https://github.com/bashrc/libdeep/blob/master/examples/cancer_classification/cancer_detection_training_error.png?raw=true" width=640/>

Installation
============

On Debian based systems:

```bash
sudo apt-get install build-essential gnuplot doxygen xdot
```

If you want to be able to visualize call graphs for development or debugging purposes then you will need to install the [egypt](http://www.gson.org/egypt) script.

On Arch based systems:

``` bash
sudo pacman -S gcc gnuplot doxygen egypt xdot
```

To build from source:

```bash
make
sudo make install
```

This creates the library and installs it into /usr/local

Unit Tests
==========

You can run the unit tests to check that the system is working as expected:

```bash
cd unittests
make
./tests
```

Or to check for any memory leaks:

```bash
valgrind --leak-check=full ./tests
```

Source Documentation
====================

To generate source code documentation make sure that you have doxygen installed and then run the generatedocs.sh script.  A subdirectory called docs will be created within which html and latex formated documentation can be found.  For general usage information you can also see the manpage.

```bash
man libdeep
```

Showing the call graph
======================

<img src="https://github.com/bashrc/libdeep/blob/master/img/callgraph.jpg?raw=true" width=640/>

If you want to visualize the call graph for a particular source file for debugging or development purposes:

``` bash
SOURCEFILE=deeplearn.c make graph
```

And you can change the *SOURCEFILE* value to whatever file you're interested in.

Examples
========

<img src="https://github.com/bashrc/libdeep/blob/master/examples/facerec/libdeep_facerec.png?raw=true" width=300/>

There are also some example programs within the examples directory. Reading the examples is the best way to learn how to use this library within your own code. Examples are:

 * Simple face recognition
 * Determining whether a cancer is malignant or benign
 * Assessing wine quality from ingredients
 * Predicting concrete quality from ingredients

Using trained neural nets in your system
========================================

You can export trained neural nets either as a C program or a Python program. These programs are completely independent and can be used either as commands or integrated into a larger software application. This makes it easy to use the resulting neural net without needing to link to libdeep. See the source code in the examples directory for how to use the export function. If you include the word "sketch" or "arduino" within the filename to be exported to then it will appear as Arduino compatible C suitable for use within an Arduino IDE rather than as standard C.

Portability
===========

Although this software was primarily written to run on Linux-based systems it's pretty much just vanilla C99 standard code and so it should be easily portable to other platforms, such as Microsoft Windows and Mac systems. The independent random number generator should mean that results are consistent across different compilers and platforms.

Packaging
=========

To build packages for Debian (deb) see https://github.com/bashrc/libdeep-debian
