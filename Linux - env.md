
### .profile
```bash
alias cdp="cd -P"
alias rmr="rm -r"
alias dss="diff -y --suppress-common-lines"
alias dff="node ~/windz/node-apps/linuxTools/cmpFolder.js"
alias ..="cd .."

export PATH=/home/windz/bin:$PATH:/home/windz/lib

psg () {
    ps aux | grep $1
}
```
