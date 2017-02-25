<p align="center">
<img src="https://raw.githubusercontent.com/KhronosGroup/glTF/master/specification/figures/gltf.png">
</p>

# COLLADA to glTF converter

A command-line tool to convert COLLADA (`.dae`) files to [glTF](https://github.com/KhronosGroup/glTF).

## Compile from source 

###1. Clone repository
 
 ```
git clone --recursive https://github.com/KhronosGroup/COLLADA2GLTF.git
```

###2. Install dependencies 

####(Debian)
 ```
apt-get install cmake libxml2-dev libpcre3-dev libpng-dev zlib1g-dev
```
####(Windows)
Install [Visual Studio](http://code.visualstudio.com)

Install [CMake](http://cmake.org/cmake/resources/software.html)

####(OSX)
Install Xcode

Install dependencies with [brew](http://mxcl.github.com/homebrew/)

```   
brew install cmake pkgconfig pcre libpng
```

if the PNG package is not found, the workaround is to Download the the *.tar.gz install from libpng and then:
```
./configure
make check
sudo make install
```

###3. Compile
####(Linux)
 ```
cd COLLADA2GLTF
mkdir linux_build ; cd linux_build 
cmake .. ; make
```
####(Windows)
```
cd COLLADA2GLTF
mkdir win_build && cd win_build
cmake .. 
```
then open COLLADA2GLTF.sln with visual studio 2015, select Release or Debug, and build

####(OSX)
```
cd COLLADA2GLTF
mkdir osx_build; cd osx_build
cmake -G Xcode ..
```
then open COLLADA2GLTF.xcodeproj and build
or if you installed xcode command line tools you can also build in the terminal: xcodebuild -target collada2gltf -configuration Release (or Debug)

###4. Run
####(Linux)
```
./bin/collada2gltf
```
####(Windows)
```
.\bin\Release\collada2gltf.exe
```
####(OSX)
```
./bin/Release/collada2gltf
```
## Usage

```
collada2gltlf -f [file] [options]
options:
-z -> path of configuration file [string]
-f -> path of input file, argument [string]
-o -> path of output file argument [string]
-b -> path of output bundle argument [string]
-g -> [experimental] GLSL version to output in generated shaders
-i -> invert-transparency
-d -> export pass details to be able to regenerate shaders and states
-p -> output progress
-l -> enable default lighting (if no lights in scene) [bool], default:true
-c -> compression type: available: Open3DGC [string]
-m -> compression mode: for Open3DGC can be "ascii"(default) or "binary" [string]
-v -> print version
-s -> experimental mode
-h -> help
-r -> verbose logging
-e -> embed resources (bin, shaders, available textures) in glTF file
-n -> don't combine animations with the same target
-k -> export materials and lights using KHR_materials_common extension
```

