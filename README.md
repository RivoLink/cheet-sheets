# cheet-sheets

## Git
```sh
git config --global user.name "RivoLink"
git config --global user.email "rivo.link@gmail.com"
git config --global credential.helper cache
```

## Start
`# start.sh`
```sh
#!/bin/bash

if [ -z "$1" ]; then
      gnome-terminal
else
      open "$1"
fi
```
`# .bash_aliases`
```sh
alias start="eval /path/to/start.sh $@"
```

```sh
# make start.sh executable
sudo chmod +x /path/to/start.sh

# refresh aliases
sudo source ~/.bash_aliases
```
