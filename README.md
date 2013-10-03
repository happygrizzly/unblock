### UnBlock

Remove 8x8-pixel "blocky" artifacts from a heavily compressed JPEG image.

### How to build on Ubuntu

`make`

### How to run on Ubuntu

`./unblock in.bmp out.bmp`

### Software used

This is a wrapper around an algorithm by [John Costella](http://johncostella.webs.com/unblock/).
His webpage includes before-and-after pictures showing the algorithm's effectiveness.

Porting John's C# source code to C/C++ was too difficult, even with Ubuntu's Mono IDE.
Instead, I started with Alexander Balakhnin's C port,
in the context of a [plugin](http://avisynth.org.ru/unblock/unblock.html)
for [AviSynth](http://sourceforge.net/projects/avisynth2/),
based on John's own 2007 C port of "the Costella libraries."

The .bmp files are read and written by [EasyBMP](http://easybmp.sourceforge.net/).
Why .bmp and not .jpg for a JPEG utility, you ask?
Because my source images are still frames from mjpeg-format video,
and when ffmpeg extracts these frames as .jpg rather than as .bmp, ffmpeg further degrades them (ick).
Also, because my later processing prefers .bmp to other formats.

### Bugs

Images whose width is not a multiple of 16 pixels may misbehave.
