# Linux for user
## *terminal*
- **terminal** is the default shell of Linux.
- The terminal have 5 parts.
1. *username*
2. *Hostname*
3. *current directory(path)*
4. *Privilege( $ and # )*
5. *Command place*

---

# **username@Hostname(path) $ = Command_place**

# **username@Hostname(path) # = Command_place**

---

## common commands shape
---

# **$ or # = Command --option argument**

---

# Commands
- *Command* is small programs that do one task well.

1. ## ls
- is used to list an items in the path.

```Git
username@Hostname(path) $ = ls
username@Hostname(path) $ = ls -l
username@Hostname(path) $ = ls -a
username@Hostname(path) $ = ls -R
username@Hostname(path) $ = ls -la
username@Hostname(path) $ = ls -lh
username@Hostname(path) $ = ls -lS
username@Hostname(path) $ = ls -ltr
```

- **ls**    ---- list directory contents
- **ls -l** ---- list files one per line
- **ls -a** ---- list all files, including hidden files
- **ls -la** --- long format list(permissions, ownership, size, etc.. ) of all files
- **ls -lh** --- long format list with size displayed using human readable unit(KB, MB, GB)
- **ls -lS** --- long format list with sorted by size(descending)
- **ls -ltr** -- long format list of all files, sorted by modified date(oldest first)

2. ## cd
- is used to change directory of the path.

```git
username@Hostname(path) $ = cd 
username@Hostname(path) $ = cd ~
username@Hostname(path) $ = cd /
username@Hostname(path) $ = cd ..
username@Hostname(path) $ = cd ../..
```

- **cd**    ---- change the directory
- **cd ~**  ---- change to the home directory
- **cd /**  ---- change to the root folder
- **cd ..** ---- back one path from the current path
- **cd ../..** - back two path from the current path

3. ## pwd
- it will print the current path.

```git 
username@Hostname(path) $ = pwd
```

4. ## mkdir & rmdir
- **mkdir** is used to create the folder(directory).
- **rmdir** is used to delete the directory.

```git
username@Hostname(path) $ = mkdir filename
username@Hostname(path) $ = rmdir filename
```

5. ## rm

```git
username@Hostname(path) $ = rm filename
username@Hostname(path) $ = rm -r filename
username@Hostname(path) $ = rm -i filename
username@Hostname(path) $ = rm -rf filename
```

- **rm**    ---- remove the files
- **rm -r** ---- Recursive removal. Allows the deletion of directories and their contents
- **rm -f** ---- Force deletion. Ignores nonexistent files and arguments, and never prompts
- **rm -i** ---- Interactive prompt before every removal

6. ## cp(copy)

```git
username@Hostname(path) $ = cp filename path
```

- **cp**   ---- copy the file to the given path(directory)

7. ## mv(move)

```git
username@Hostname(path) $ = mv filename path
```

- **mv**    ---- move the file(directory) to the given directory

8. ## echo

```git
username@Hostname(path) $ = echo "text" 
username@Hostname(path) $ = echo "text" > filename
username@Hostname(path) $ = echo "text" >> filename
```

9. ## cat/head/tail/less

```git 
username@Hostname(path) $ = cat filename
username@Hostname(path) $ = head filename
username@Hostname(path) $ = tail filename
username@Hostname(path) $ = less filename
```

- **cat**   ---- print the file
- **head**  ---- print the upper(head) part of the file, by the default 10 lines.
- **tail**  ---- print the lower(tail) part of the file.
- **less**  ---- print the file, but file appear in less than cat command

10. ## grep(search and filter)

```git
username@Hostname(path) $ = grep "name" file || cat filename | grep "name"
username@Hostname(path) $ = grep -i
username@Hostname(path) $ = grep -c
username@Hostname(path) $ = grep -l
username@Hostname(path) $ = grep -R
username@Hostname(path) $ = grep -v
username@Hostname(path) $ = grep -n
```

- **grep -i**   ---- case insensitive
- **grep -c**   ---- count word
- **grep -l**   ---- display filename
- **grep -R**   ---- search text in folders
- **grep -v**   ---- display without this term
- **grep -n**   ---- display the term find number

11. ## wc(word count)

```git
username@Hostname(path) $ = wc filename
username@Hostname(path) $ = wc -c
username@Hostname(path) $ = wc -w
username@Hostname(path) $ = wc -m
username@Hostname(path) $ = wc -l
```

- **wc -c**  ---- count the bytes
- **wc -w**  ---- count the words
- **wc -m**  ---- count the characters
- **wc -l**  ---- count the lines

# Multiple command
1. and(&&)
2. or(||)
3. piping(|)