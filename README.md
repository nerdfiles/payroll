# Resizing Source Payroll Scans

## Sizes

Standard personal check are 6" x 2 and 3/4".

## Notes

What's required is that the Program uses ImageMagick which requires 
GhostscriptXPS to be part of the DELEGATE list of ImageMagick so that 
file conversion is possible[0] via ImageMagick. But this is not easily 
done, so I am using the following Homebrew formula to install libgxps 
to work with a GNOME-based converter.

1. https://github.com/GNOME/libgxps

Typically ImageMagick would be installed with the --with-gslib flag so that 
the DELEGATE list properly includes the right binaries.

2. brew install gs # ghostscript
3. brew install imagemagick

## With ImageMagick

### Stuff

    -resize 100x40
    -flip           # vertical
    -flop           # horizontal
    -transpose      # flip vertical + rotate 90deg
    -transverse     # flip horizontal + rotate 270deg
    -trim           # trim image edges
    -rotate 90

### Resize to fit

    convert input.jpg -resize 80x80^ -gravity center -extent 80x80 icon.png

### Convert all images to another format

    mogrify -format jpg -quality 85 *.png

### Make a pdf

    convert *.jpg hello.pdf
