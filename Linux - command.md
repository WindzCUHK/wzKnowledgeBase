# vim replace
```
:%s/^\(.\)/#\1/
```

# crop file by line
```bash
sed -n '8,12p' yourfile
```

# push pop dir
```bash
pushd
popd
```

# folder file cmp
```bash
diff -rq folder-1 folder-2
```

# check linux version
```bash
uname -a
cat /proc/version
cat /etc/*release
```

# tar
```
-c create tar file
-t display tar info
-x unpack tar file
-f set tar file name
-v verbose
-z use gzip
```

# decompress
```bash
bzip2 -d {file}
tar -zxvf {file}
unzip {file}
```

# compress
```bash
zip -r {target.zip} {source1, ...}
```

# process
```bash
ps -u {username}
top
kill {PID}
kill -9 {PID}
```

# user related
```bash
finger {user} # display user info
yppasswd # change unix pw
talk {user}
```

# dictionary
```bash
webster {word}
```

# search all files in path by text "pattern"
```bash
grep --include=\*.{c,h} --exclude=*.o --exclude-dir={dir1,dir2,*.dst} -rnw '/path/to/somewhere/' -e "pattern"
```

# crontab all user (root reuqired)
```bash
for user in $(cut -f1 -d: /etc/passwd); do echo $user; crontab -u $user -l; done
```

# check disk space
```bash
df -h
```

# copy files to multi folder
```bash
echo dir1 dir2 dir3 | xargs -n 1 cp file1
```

# netstat
```bash
(cat /proc/sys/net/ipv4/ip_local_port_range | cut -f 1 | sed 's/\(.*\)/\1     ***** BEGIN dynamic port *****/'; cat /proc/sys/net/ipv4/ip_local_port_range | cut -f 2 | sed 's/\(.*\)/\1     ***** END dynamic port *****/'; netstat -nap | grep "LISTEN " | sed 's/.*:\(\w.*\) .*:.*LISTEN\W*\(.*\)/\1     Listen by process \2/') | sort -n
```

# SSH tunnel
```bash
ssh -L 0.0.0.0:50005:172.19.19.101:50007 gofix@172.19.19.101 -N
ssh -R 0.0.0.0:50005:172.19.19.101:50007 gofix@172.19.19.101 -N
```

# recursively find and list the latest modified files in a directory with subdirectories and times
```bash
find $1 -type f -exec stat --format '%Y :%y %n' "{}" \; | sort -nr | cut -d: -f2- | head
# don't support files with white spaces in the names
find $1 -type f | xargs stat --format '%Y :%y %n' | sort -nr | cut -d: -f2- | head
```

# diff irectory trees
```bash
diff --brief -r dir1/ dir2/
# see differences for files that may not exist in either directory
diff --brief -Nr dir1/ dir2/
```
