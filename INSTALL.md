# OpenEmulator installation instructions

These are developer instructions for building OpenEmulator. Users should download a pre-packaged [release](https://openemulator.github.io/) that is ready to use.

## macOS
We aim to be portable, but currently the only officially supported and tested platform is macOS.

To compile OpenEmulator for macOS you need Xcode and several external libraries not available by default. The simplest way to install them is using Homebrew.

### Setup
After cloning this repository, `cd` into it and retrieve the libemulation sources:

	git submodule update --init --recursive

### Dependencies
Install the dependencies for libemulation as described [here](https://github.com/openemulator/libemulation/blob/master/INSTALL.md). When the dependencies are installed, build libemulation:

	cmake -Hmodules/libemulation -Bmodules/libemulation/build -DCMAKE_BUILD_TYPE=Release
	cmake --build modules/libemulation/build --config Release

### Build
Open OpenEmulator in Xcode to build, or run one of these commands:

    ./build_openemulator (builds a dynamically linked application)
    ./build_openemulator-standalone (embeds required libraries in the application)
    ./build_openemulator-universal (builds a stand-alone universal application)
	(deprecated) xcodebuild -arch x86_64
	(deprecated) xcodebuild -arch arm64

These commands will create the application bundle `OpenEmulator.app` in the build/Release directory.
