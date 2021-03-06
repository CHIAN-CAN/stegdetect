stegdetect
==========

Stegdetect is an automated tool for detecting steganographic content in images.

This repo has been updated to compile cleanly on Ubuntu since the original project appears to be abandoned and no longer accepts pull requests.

Tested on Ubuntu 16.04 and 18.04 only(17.x likely works though)

### Building on 64-bit Systemgs

```bash
    $ linux32 ./configure
    $ linux32 make
```

You can now run stegdetect from the local directory: `./stegdetect`

### Build for Android

This Android build is sort of fragile, there are many compile warnings.

You must set the environment variable `NDK_BASE` to the root location of your
Android NDK.

```bash
    $ make clean
    $ make -f Makefile.android
```

### Usage

Stegdetect does two types of F5 detection, simple and "slow". Simple merely
looks for a comment in the header, which any savy coder has removed. This
method is enabled with the "`-tf`" option.

The "slow" F5 detection is enabled with "`-tF`"

To run detection on a directory of JPEGs use:

```bash
    for img in `find /path/to/images/ -iname "*jpg"`; do
        ./stegdetect -tF $img;
    done
```

**Android**


```bash
    $ adb push stegdetect /data/local/tmp
    $ adb shell
        for img in `ls /sdcard/PixelKnot/*jpg`; do
            /data/local/tmp/stegdetect -tF $img
        done
```
