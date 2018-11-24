---
tutorial: "Command Line Fundamentals"
section: "Filters"
author: Dennis Tenen
update: "5/29/15"

---

## Filters

```
sort
uniq
grep
head
tail
tr
sed
awk
shuf
fmt
look
pr
```

### Findly
```
find . -name "*.md"
grep ly
wc
grep ly | wc
sort test.md | uniq -c
```

### Turning day into night
```
sed 's/day/night/' 24hr.txt
echo day | sed s/day/night/
sed -i .bak 's/day/night/' 24.txt
sed 's/day/night/' 24hr.txt
```
### Putting all your eggs in one basket
```
find . -type f -name "*.md" | xargs grep "orange" | sed s/orange/apple/ >> apple.txt
```

### Rewriting Moby Dick
```
cat pg2701.txt | sed 's/\s/\n/g' | sort | uniq -c | sort -hr > test.txt
find . -name "test*" | xargs sed -i 's/apple/orange/g'
or find . -name "test*" -exec sed -i 's/apple/orange/g'
```

### Parse column data 

```
# note the two spaces to make it more challenging
echo "column1-1  column1-2  column1-3" > test.txt
echo "column2-1  column2-2  column2-3" >> test.txt
echo "column3-1  column3-2  column3-3" >> test.txt

cat test.txt
cat test.txt | tr -s ' ' | cut -d' ' -f2

# try it without the tr to see what happens
```
