---
layout: lesson
lesson-id: command-line-001
title: "Unit 1: Conversing in Plain Text"
authors: Dennis Yi Tenen
---

# Files, Paths, & Folders

![Anatomy of a UNIX Command.](http://sc.tamu.edu/help/general/unix/cmd-anatomy.jpg)

> *Figure 1* Anatomy of a UNIX Command. Via
[Texas A\&M High Performance Research Computing](http://web.archive.org/web/20150529023907/http://sc.tamu.edu/help/general/unix/unix.html)

## Follow Along

```
man man
mkdir
base64 /dev/urandom | head -c 10000000 > file.txt
cp oldpath/oldfile newpath/newfile
mv oldpath/file newpath/file
rm -i path/filname
rm -r foldername
cat filename
head filename
tail filename
man rename
man split
man file

man df
df -h

cat mypaper.doxc

```

## Your Turn

```
# Create three directories

# Download several files into them

# rename the files

# see what happens when you move one file into the other

```

**Bonus!**  

```
# explore one of your word files
unzip -qc mypaper.docx > mypaper.xml
```

**Notes**: File names are case sensitive. Think of the syntax as "verb, adverb,
object noun". What separates these? Blank space. What happens to blank space in
file names? For this reason, it is good hygiene not to use spaces or capitals
when naming files. Rename with `mv`. Open your graphical file manager and
follow along as you move / create / delete files. `cat` a `.pdf` file, `.docx`,
and `.txt`. `rm` is dangerous! Consider creating an `archive/` folder and using
`mv` instead of `rm` for a safer alternative. The `-i` flag will ask for
confirmation at least.

**Explore**: [Take the Linux Filesystem Tour](http://web.archive.org/web/20140224004333/http://tuxradar.com/content/take-linux-filesystem-tour#null)

**Bonus**: `ctr+shift+R [start typing one of the commands you used above]`, repeat to
cycle through
