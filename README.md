#CorsixTH Graphics Project

![](http://i.imgur.com/fYp148T.jpg)
### Latest Status [![Build Status](https://travis-ci.org/CorsixTH/CorsixTH-Graphics.svg?branch=master)](https://travis-ci.org/CorsixTH/CorsixTH-Graphics)

##### [Desired Assets](https://github.com/CorsixTH/CorsixTH-Graphics/New-Assets) | [Forum](http://forums.corsixth.com) | [IRC Chat](http://webchat.freenode.net/?channels=corsix-th) | [Report Issue](https://github.com/CorsixTH/CorsixTH-Graphics/issues/new) <!-- [![Windows Build Status](https://ci.appveyor.com/api/projects/status/github/CorsixTH/CorsixTH-Graphics?branch=master&svg=true)](https://ci.appveyor.com/project/TheCycoONE/corsixth-Graphics) -->

This project aims to replace the original graphics from Theme Hospital that are currently used in CorsixTH.
So far the following artists have made contributions:

- Zephyris

---

#####How to build the program:

1. Confirm or install the requirements (libpng and a C++ compiler - g++, XCode, Visual Studio or MinGW)
2. Clone or download this repository
3. Enter the AnimationEncoder folder in a terminal
4. Run *make*. Optionally specify the C++ standard, e.g. *make CCFLAGS="-std=c++14"*
5. Optionally run *make docs* for documentation (requires doxygen) or *make clean* to remove build files

---

#####How to use new sprites:

1. Compile a graphics file by *./AnimationEncoder/encoder ground_tiles.txt ground_tiles* (replace with the specification file and chosen output filename)
2. Instruct CorsixTH to use the new graphics by enabling it in the config file and specifying the new file (not yet supported)
3. Enjoy the different-looking game!

---

#####How to submit new sprites:

1. Create new images
2. Create the specification file (details in *manual.html*)
3. Create the graphics file
4. Play through CorsixTH using this file to check that it works (not yet supported)
5. Create a PR containing the images and specification file
6. Optionally add the compile graphics command to *.travis.yml*

Alternatively submit materials, complete or in progress, to the forums or IRC.

---

#####Key Links

- [CorsixTH Graphics Wiki](https://github.com/CorsixTH/CorsixTH-Graphics/wiki)
- [CorsixTH Coding Conventions](https://github.com/CorsixTH/CorsixTH/wiki/Coding-Conventions)
- [CorsixTH Code Documentation Style](https://github.com/CorsixTH/CorsixTH/wiki/CodeDocumentationStyle)
- [CorsixTH Rendering](https://github.com/CorsixTH/CorsixTH/wiki/Rendering)

#####Contact Details

- [CorsixTH homepage](http://forums.corsixth.com/)
- [CorsixTH forums](http://forums.corsixth.com/)
- [Google Developer group](http://groups.google.com/group/corsix-th-dev)
- IRC #Corsix-TH on irc.freenode.net
