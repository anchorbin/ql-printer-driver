# About #

This program prints 1083 by 336 pixel monochrome PNG files on the Brother QL-570 thermal sticker printer by writing to the Linux device file (e.g. /dev/usb/lp0).

# Prerequisites #

You need libpng and the libpng header files in order to compile. To install the required packages on a Debiab-based system:

```
sudo aptitude install build-essential libpng12-0 libpng12-dev
```

# Compiling #

Simply run:

```
make
```

# Usage #

```
Usage: ./ql570 printer n|w pngfile [cutoff]
  Where 'n' is narrow paper (29 mm) and 'w' is wide paper (62 mm).
  [cutoff] is the optional color/greyscale to monochrome conversion cutoff (default: 180).
  Example: ./ql570 /dev/usb/lp0 n image.png
  Hint: If the printer's status LED blinks red, then your media type is probably wrong.
```

If you feed try to print a greyscale or monochrome PNG, then it will be converted to monochrome before printing. The image is converted by turning all pixels that have a value of less than 180 out of 255 in either color channel black, and the rest white. The cutoff can be adjusted to something other than 180 by specifying it on the command line.

# Credit #

Asbjørn Sloth Tønnesen reversed engineered the QL-570 protocol and wrote all the important parts of this program.

Marc Juul added support for different paper sizes and conversion cutoff.