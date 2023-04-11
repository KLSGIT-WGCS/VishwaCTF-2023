# Steganography
- Challenge Name : Guatemala
- Difficulty :  Easy

## Challenge Description
My friend wanted to install an antivirus for his computer, but the creator of the antivirus was caught!

## Methodology
A .gif file was provided with the challenge. A seemingly normal gif with absolutely nothing hidden in it (or was there).

We first ran [Exiftool](https://github.com/exiftool/exiftool) on the gif. Exiftool is an open-source tool that can be used for reading and writing metadata(some extra data about the image size,version etc) to a variety of files. Doing this gave us the following results:

ExifTool Version Number         : 12.57
File Name                       : AV.gif
Directory                       : ..
File Size                       : 1112 kB
File Modification Date/Time     : 2023:04:01 12:43:55+05:30
File Access Date/Time           : 2023:04:02 14:30:03+05:30
File Inode Change Date/Time     : 2023:04:01 12:43:55+05:30
File Permissions                : -rw-r--r--
File Type                       : GIF
File Type Extension             : gif
MIME Type                       : image/gif
GIF Version                     : 89a
Image Width                     : 498
Image Height                    : 498
Has Color Map                   : Yes
Color Resolution Depth          : 8
Bits Per Pixel                  : 8
Background Color                : 0
Animation Iterations            : Infinite
**Comment                         : dmlzaHdhQ1RGe3ByMDczYzdfdXJfM1gxRn0=**
Frame Count                     : 17
Duration                        : 2.04 s
Image Size                      : 498x498
Megapixels                      : 0.248

Note the boldened attribute, it seems a bit fishy. The value of the comment seems to be a base64 encoded string. We then used an online base64 decoder (there's plenty) and voila ! we have our flag !!

> vishwaCTF{pr073c7_ur_3X1F}

Tip: base64 encoded strings will ***usually*** end with the '=' sign (Why? Research abou it!). That's how you can figure out that it is encoded in base64 !!`