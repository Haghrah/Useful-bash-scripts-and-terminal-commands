## Useful-bash-scripts-and-terminal-commands
A collection of useful bash scripts and terminal commands for Ubuntu


### Converting files

* Convert PDF file to a set of JPG images
```
convert -verbose -density 600 -trim slides.pdf -quality 100 -flatten slides.jpg
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


