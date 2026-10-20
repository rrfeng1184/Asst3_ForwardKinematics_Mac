# Forward Kinematics

## Getting started
We will be distributing assignments with git. You can find the repository for this assignment at https://github.com/rrfeng1184/Asst3_ForwardKinematics_Mac If you are unfamiliar with git, here is what 
you need to do to get the starter code:
```
$ git clone https://github.com/rrfeng1184/Asst3_ForwardKinematics_Mac.git
```
This will create an asst2_CubicCurve_mac folder with all the source files.


## Build Instructions

To build your code for this assignment:
```
$ cd Asst3_ForwardKinematics_Mac && mkdir build && cd build
$ cmake ..
$ make
```

These steps (1) create an out-of-source build directory, (2) configure the project using CMake, and (3) compile the project. If all goes well, you should see an executable app in the build directory. As you work, simply typing make in the build directory will recompile the project. 

If you run into multiple errors during the cmake/make: modify the minimum required cmake version in the corresponding cmake file that reports the error; if you see error related to NanoGui, go to NanoGui cmake file and remove "PREBUILD"; if you wee error related to glfw, go to glfw->src->cmakelist.txt and add the following:

```
if (APPLE)
    set_source_files_properties(
        nanogui/ext/glow/src/cocoa_init.m
        nanogui/ext/glfw/src/cocoa_monitor.m
        nanogui/ext/glfw/src/cocoa_window.m
        nanogui/ext/glfw/src/nsgl_context.m
        PROPERTIES COMPILE_FLAGS "-fno-objc-arc"
    )
endif()
```

The configure the project using CMake is done already and thus you only need to run "make" to compile the project. If all goes well, you should see an executable app in the build directory. As you work, simply typing ```make``` in the build directory will recompile the project.

### Run

When you have successfully built your code, you will get an executable named **helloworld**. The helloworld executable do not take any argument. 

To run your executable file:
```
# under build folder
$ ./asst
```




--- 

## FAQ / Dependencies / Troubleshooting

There are several dependencies we need to rely on, but for most of them you do not need to do anything, we've configured all of them through CMake. This section is just for you to be aware of these dependencies. If you have any issue during building process, please double check following dependencies before coming to TA's office hour.


#### 1. C++11 and OpenGL

You **DO NOT** need XCode for this assignment, although **Command Line Tools** is required.
These two should already setup in MacOS by default. You can verify by running:
```
# shows gcc version
$ gcc -v 

# shows "/Library/Developer/CommandLineTools"
$ xcode-select -p

# if swith from xcode to CLT
$ sudo xcode-select -s /Library/Developer/CommandLineTools

# if not installed, then run
$ xcode-select --install
```

#### 2. GLEW

We provide GLEW in our library (under ``deps`` folder), therefore, you **DO NOT** need to do anything. 

However, some might encounter follwing issue during while running  ```make```:
```
ld: library not found for -lglew
```
and one possible solution (from StackOverlow [post](https://stackoverflow.com/questions/26430432/ld-library-not-found/26431115#26431115)), add following line to file ```~/.bash_profile```:
```
# double check your glew location
# ATTENTION: version number might be different!!!!
export LIBRARY_PATH="$LIBRARY_PATH:/usr/local/Cellar/glew/2.1.0_1/lib/"
```
then run source to execute the change:
```
source ~/.bash_profile
```

If you want to use system GLEW, you can run following command to install GLEW then update CMakeLists.txt ON YOUR OWN.
```
######## OPTIONAL ########
$ brew install glew
# remember to update CMakeLists.txt
######## OPTIONAL ########
```

#### 3. NanoGUI

We setup these dependencies in our cmake/modules/*.cmake files, therefore, you **DO NOT** need to do anything about it.


#### 4. GLFW

We will use the GLFW provided in NanoGUI, therefore, you **DO NOT** need to do anything. 

However, If you want to use system GLFW, you can run following command to install GLFW then update CMakeLists.txt ON YOUR OWN.
```
######## OPTIONAL ########
$ brew install glfw3
# remember to update CMakeLists.txt
######## OPTIONAL ########
```

#### GLM

We setup these dependencies in our cmake/modules/*.cmake files, therefore, you **DO NOT** need to do anything about it.


However, If you want to use system GLM, you can run following command to install GLM then update CMakeLists.txt ON YOUR OWN.
```
######## OPTIONAL ########
$ brew install glm
# remember to update CMakeLists.txt
######## OPTIONAL ########
```

## Resources and Notes

- [Rasterization Rules in Direct3D 11](https://msdn.microsoft.com/en-us/library/windows/desktop/cc627092(v=vs.85).aspx)
- [Rasterization in OpenGL 4.0](https://www.opengl.org/registry/doc/glspec40.core.20100311.pdf#page=156)
- [Bryce Summer's C++ Programming Guide](https://github.com/Bryce-Summers/Writings/blob/master/Programming%20Guides/C_plus_plus_guide.pdf)
- [NeHe OpenGL Tutorials Lessons 01~05](http://nehe.gamedev.net/tutorial/lessons_01__05/22004/)

## Acknowledge

This repo also use **DownloadProject** (https://github.com/Crascit/DownloadProject) for downloading and configuring NanoGUI (including GLFW) and GLM. 

