## Useful links
- [linux sysops handbook](https://abarrak.gitbook.io/linux-sysops-handbook/)

## Check Storage in server
List the storage of directories
```bash
sudo df -h
```
List the store of everyone 
```bash
# cd to the directory you wish to check
sudo du -h -s * | sort -h
```
List the storage used of everyone even hidden files
```bash
sudo du -h -s .[^.]* | sort -h
```

## Find a file 
```bash
find <dir> -iname <file name>
# e.g. find ~ -iname <*.txt> show all the full paths of file with extension .txt
```
## Find a file based on content
```bash
find . -type f -exec grep "content to match" '{}' \; -print
# Goes thru all files in current dir (.) of type file (-type f) greps the content and prints. The curly braces ({}) are a placeholder for those results matched by the Linux find command. The {} go inside single quotes (‘) so that grep isn’t given a misshapen file name. The -exec command is ended with a semicolon (;), which also needs an escape (\;) so that it doesn’t end up being interpreted by the shell.

find . -type f -print | xargs grep "forinstance"
# Another option but using xargs
```

## ps
Process status, information about processes running in memory.
[more info](https://ss64.com/bash/ps.html)
```bash
ps -ef | grep docker
```
- `-e`: Select all processes, including those of other users.
- `-f`: Full-format listing

## Linux : How to gzip a folder
```bash
tar -cvzf outputfilename foldertocompress
# e.g. tar -cvzf meow.tar.gz meow/
```

## Rename files
```bash
for file in *.png; do mv "$file" "${file/_h.png/_half.png}"; done #  ${string/substring/substitution}
```

## Getting the top levels
```bash
grep -E '^ {2}"' example.json # grabs all first 2 leading spacing things
grep -E '^ {2,6}"' example.json # grabs all the things between 2 and 6 spacings
```

## Check for the PID that is using a specific port
```bash
sudo lsof -i :PORTNUMBER
```

## Check for the PID using a range of ports
```bash
sudo lsof -i:PORT_START-PORT_END
# e.g. sudo lsof -i:8001-8030
```

## Kill PIDs using a specific port
```bash
sudo kill -9 `sudo lsof -t -i:8001` # note to use the backticks
sudo kill -9 $(sudo lsof -t -i:8001) # you can also use the command interpolation
```
## Check where a PID is ran from
```bash
ll /proc/>PID>/cwd
e.g. ll /proc/31231/cwd
```

## Check ubuntu version
```bash
lsb_release -a
```

## Count the number of files in a directory
```bash
ls <directory> | wc -l
```

## Getting your ip
```bash
curl ip.sb
```
Check out their website at https://ip.sb/