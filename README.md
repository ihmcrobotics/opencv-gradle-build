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
Download and install the [Java JDK](http://www.oracle.com/technetwork/java/javase/downloads/index-jsp-138363.html).

The [Homebrew](https://brew.sh) package manager is the recommended way of getting the other dependencies on macOS. After
installing Homebrew, open a terminal and run the following commands:
```bash
brew install python cmake ant
```

#### Windows
For Windows, be sure to follow the install instructions completely. Most of these packages will require you to edit environment
variables as part of the installation process.
- Download and install the [Java JDK](http://www.oracle.com/technetwork/java/javase/downloads/index-jsp-138363.html).
- Download and install [Python](https://www.python.org)(version 2.7 or >=3.5).
- Download and install [Ant](http://ant.apache.org/manual/install.html).
- Download and install [Visual Studio Community 2017](https://www.visualstudio.com/). During installation, make sure the 'Desktop development
with C++' workload is selected.

## Compile and generate Java wrapper
After checking out the `opencv` and `opencv_contrib` source and downloading the build dependencies above, you're ready to compile
OpenCV into a static library and generate the Java wrapper. In Ubuntu or macOS open a terminal, Windows open the Developer Command
Prompt for VS 2017, and change directory into where you've cloned this repository. Run the following command matching your OS to
compile and publish OpenCV JARs to a local Maven repository.

**Ubuntu and macOS**
```bash
./gradlew publishToMavenLocal
```

**Windows**
```bash
gradle.bat publishToMavenLocal
```

## Publishing to Bintray
There is also a block for publishing the generated artifacts to Bintray. To publish the platform independent Java wrapper,
set `bintrayPublishType` in the `gradle.properties` file equal to `WRAPPER` and run the `bintrayUpload` Gradle task. To publish
a JAR containing the OpenCV static library for your OS, set `bintrayPublishType` to `PLATFORM` and run the `bintrayUpload`
Gradle task. You'll also need to add `bintray_user` and `bintray_key` variables to the `gradle.properites` if they aren't
set in your global Gradle properties already.

**Ubuntu and macOS**
```bash
./gradlew bintrayUpload
```

**Windows**
```bash
gradle.bat bintrayUpload
```