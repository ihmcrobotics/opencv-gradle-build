# OpenCV Gradle Build

This repo provides a Gradle interface for compiling OpenCV static libraries and wrapper JARs for Windows, macOS, and Ubuntu,
as well as publishing them to Bintray. The resulting JARs are intended to be used with [IHMC's Native Library Loader](https://github.com/ihmcrobotics/ihmc-native-library-loader).

## Getting the OpenCV source
As a convenience, the official `opencv` and `opencv_contrib` repositories are added as Git submodules. For tagged releases,
submodules will match the version of this repository i.e. tag x.y.z of this repo will contain submodules pinned at x.y.z. To
get all of the necessary source code for building: cloning this repository, go into the target directory and update the submodules:
```bash
git clone https://github.com/ihmcrobotics/opencv-gradle-build.git
cd opencv-gradle-build
git submodule update --init --recursive
```

## Setting up your build environment
There are several things you need to have installed in order to compile OpenCV. Namely:

- Java JDK
- Python (2.7 or >=3.5)
- CMake
- C/C++ compiler
- Ant

The following sections will detail setting up a working build environment for each supported operating system.

**Note:** currently only 64-bit operating systems are supported.

#### Ubuntu
Open a terminal and run the following commands:
```bash
sudo apt install build-essential openjdk-8 python ant
```

#### macOS
Download and install the Java JDK from [Oracle's website](http://www.oracle.com/technetwork/java/javase/downloads/index-jsp-138363.html).

The [Homebrew](https://brew.sh) package manager is the recommended way of getting the other dependencies on macOS. After
installing Homebrew, open a terminal and run the following commands:
```bash
brew install python cmake ant
```

#### Windows
Download and install the Java JDK from [Oracle's website](http://www.oracle.com/technetwork/java/javase/downloads/index-jsp-138363.html).



## Generate Java wrapper

## Compile native library

## Publishing
