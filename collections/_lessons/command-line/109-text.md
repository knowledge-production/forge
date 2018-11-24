---
tutorial: "Command Line Fundamentals"
section: "Text Manipulation"
author: Dennis Tenen
update: "5/29/15"

---

## Text manipulation

```
cut
paste
join
strings
```

### Popping the hood

```
wget http://link/moby.pdf OR
curl -O link/moby.pdf
pdftotext moby.txt``
cat moby.txt
cat moby.pdf
clear
xxd moby.txt
xxd moby.pdf
echo "how many words does it take?" > test.txt
wc -w test.txt
wc -l test.txt
wc -m test.txt
man wc
```

### Putting all your fruits into one basket

> lines and words, destructive vs. non-destructive transformations
> (munging), more pipes

1. add your fruits  
`   echo "orange banana pear tomato banana pear orange apple apple strawberry nectarine" > fruit.txt`

2. add another one  
`    echo "banana" >> fruit.txt`

3. substitute space for newlines  
`    cat fruit.txt | tr ' ' '\n'`

4. remove bad fruit  
`    echo "nectarine" > bad-fruit.txt`  
`    echo "tomato" >> bad-fruit.txt`  
`    cat fruit.txt | grep -vf bad-fruit.txt`  
`    cat fruit.txt` (to see if it worked)  

5. sort and count  

`    sort fruits.txt > sorted-fruits.txt`  
`    uniq -c sorted-fruits.txt`  

### Hunting the Whale 

> dataflow programming, bag of words, tokens vs. types

```bash
# make a project directory where we experiment
mkdir hunting-whale

# cd into the directory
cd hunting-whale

# let's grab moby dick (or use another novel"
# make sure it is in plain text!
# the angle bracket is a redirect into a file
curl http://www.textfiles.com/etext/FICTION/melville-moby-106.txt > moby.txt

# let's peek inside
cat moby.txt

# find the whale
grep "whale" moby.txt

# substitute whale for chicken globally
cat moby.txt | sed 's/whale/chicken/g' > chicken.txt

# see what happened to the whales
grep "chicken" chicken.txt

# remove punctuation.
cat moby.txt | tr -d "[:punct:]" > moby-nopunct.txt

# check if it worked
tail moby-nopunct.txt

# translate all upper case into lower
cat moby-nopunct.txt | tr '[:upper:]' '[:lower:]' > moby-clean.txt
tail moby-clean.txt

# sort by word frequency
cat moby-clean.txt | tr ' ' '\n' | sort | uniq -c | sort -hr > word-count.txt`

# see what we did there
head word-count.txt

# explore the word frequency list
# what rank does the word "whale" have? 

grep -nw whale word-count.txt

# what respective ranks do gendered pronouns have? 

grep -nw he word-count.txt
grep -nw she word-count.txt
```

###A Whale of a Function 

Let's put this all together into a function, so we don't have to run so many commands: 

`function wordfrequency { cat $1 | tr -d "[:punct:]" | tr '[:upper:]' '[:lower:]' | tr ' ' '\n' | sort | uniq -c | sort -hr }`

This function allows you to run `wordfrequency moby.txt` and see a word frequency list. To scroll through it, you can pipe it through less: `wordfrequency moby.txt | less`. To write it to a file, you can run something like: `wordfrequency moby.txt > moby-wordfrequencies.txt`. 

If you want to be able to save your `wordfrequency` function so that you can run it later, add the function declaration to your `.bashrc` file if you use Linux, or your `.bashprofile` file if you use MacOS. 

**Explore:** [My Advisor Rewrote Himself in Bash](http://web.archive.org/web/20150623031217/http://matt.might.net/articles/shell-scripts-for-passive-voice-weasel-words-duplicates/)
