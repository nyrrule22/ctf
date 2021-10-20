# Enumeration

## Steps

### Checks

* Check for extension file type if not familiar
* Open up file based on what type of file it is
  * Check for any interesting plaintext information
* Find out how to execute the file if applicable
  * Ex: `.gcode` file, found and used CAMotics to execute

## Tools

### Strings

The strings command looks for printable strings in a file.

### ExifTool

ExifTool is a free and open-source software program for reading, writing, and manipulating image, audio, video, and PDF metadata.

### CAMotics

CAMotics is an Open-Source GCode simulator which simulates 3-axis CNC.

## File Types

### .gcode

A GCODE file contains commands in G-Code, which is a language used to describe how a 3D printer should print a job.

#### Execute .gcode file

Open up the .gcode file in CAMotics and press play.

### .apng

APNG is an extension of the [PNG](http://www.w3.org/TR/PNG/) format, adding support for animated images.

#### Splitting the APNG file

Let's split it into the different png images. To do this we use the tool APNG Disassembler

`sudo apt-get install apngdis`

`apngdis <file-name>.apng`

Might be able to zoom in on findings.

When extracting the frames from an Animated PNG using apngdis, you’ll get 2 files for each frame. One PNG and a TXT file containing all metadata, like the timing for each frame. We can extract that with a bit of cutting.

`cat apngframe*.txt | cut -f2 -d= | cut -f1 -d/ | tr "\n" " "`

Converting the hex output to ASCII strings could result in a flag.

May also be able to utilize a Hex reader.

### .mp4

An MP4 file is a multimedia file that stores a movie or video clip and may also contain subtitles, images, and metadata.

To make the timing of the durations that the LED is on and off a little easier load the mp4 up in Adobe Premiere and zoom in on the video in such a way that the LED fills the entire screen.

Can use ffmpeg to split the video in "scenes"

`ffmpeg -y -i boardRecording_zoom.mp4 -vf yadif -c:v libx264 -profile:v high -preset:v fast -x264opts min-keyint=15:keyint=1000:scenecut=20 - b:v 2000k -c:a aac -b:a 128k -f segment -segment_format mp4 -segment_time 0.01 -segment_format_options movflags=faststart output%05d.mp4`

Now, we can query the duration of each individual clip and look for anomolies

``for FILE in `ls output*.mp4`; do echo $FILE; ffmpeg -i $FILE 2>&1 | grep Duration | cut -f1 -d, | cut -f2- -d: ; done``

We can load the result in LibreOffice Calc, round each second and compare to a bit starting with 0. Getting the results from each row and putting them in one long binary string, it can be converted to ASCII, which may reveal a flag.
