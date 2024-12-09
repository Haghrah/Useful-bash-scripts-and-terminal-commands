## Useful-bash-scripts-and-terminal-commands
A collection of useful bash scripts and terminal commands for Ubuntu


### Converting files

* Convert PDF file to a set of JPG images
```
convert -verbose -density 600 -trim slides.pdf -quality 100 -flatten slides.jpg
```

* Convert .webp to *.png
```
for file in *.webp; do
    dwebp "$file" -o "${file%.webp}.png"
done
```

### SSH

* Copy file using SSH
```
scp [file name] [user name]@[ip address]:~/[destination]
```

### Meta data

* Get image metadata
```
exiftool image1.jpg
```

### FFMPEG

* Removing the audio channel from a mp4 file
```
ffmpeg -i input.mp4 -an -c:v copy output.mp4
```

### Latex

* Word count in the output pdf
```
texcount -sum -1 file.tex
```







