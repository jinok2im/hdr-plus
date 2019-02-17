Note: The user "Titaniumtown" is now the primary maintainer of this repository; if you need to contact the owner contact "Titaniumtown".

# HDR+ Implementation
Please see: http://timothybrooks.com/tech/hdr-plus

Original Document on the subject (by Timothy Brooks): http://timothybrooks.com/tech/hdr-plus

To compile, follow these steps:
1. Install libraw¹, libpng, and libjpeg.²
2. Download a version of Halide³ from https://github.com/halide/Halide_old_history/releases.
3. Set `HALIDE_ROOT_DIR` in CMakeLists.txt to the Halide directory path.
4. From the project root directory, run the following commands:
```
mkdir build
cd build
cmake ..
make
```

Height and Width related errors:

If you get an error relating to the width and height of the input photos⁴ change the width and height in src/HDRPlus.cpp to the dimensions of your input files.

  Example of an error created:
  ```
  Input image '/Users/simon/Desktop/Photography/HDR-PLUS-TEST/1//3.dng' has width 3474, but must must have width of 5796
  ```

Usage:
```
./hdrplus [-c comp -g gain] dir_path out_img raw_img1 raw_img2 [...]
```

The -c and -g flags change the amount of dynamic range compression and gain respectively. Although they are optional because they both have default values. 

Footnotes:

¹ If you are on macOS the included dcraw binary will not work so I included the macos version in the same directory. If you are on macOS change the following "../tools/dcraw" to "../tools/dcraw_macos" in the files below before compiling:
  - batch_dcraw.py
  - finish.cpp (2 instances)
  - HDRPlus.cpp
  - halide_load_raw.h
  
² Also to install libraw, libpng, and libjpeg on macOS run ```brew install libraw* libpng* libjpeg*```

³ The exact version of Halide to be used will be determined as I am still testing different versions. If you know of a specific version feel free to contact me.

⁴ I am looking into the program automaticly finding the width and height of the input photos. If you have any pointers please contact me Titaniumtown.
