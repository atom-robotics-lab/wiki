# Installation of virtual environment wrapper and creating a virtual enviornment : 

## To install virtualenvwrapper

```shell
pip install virtualenvwrapper
```

## To open .bashrc

```shell
nano ~/.bashrc
```

## Paste these lines in the .bashrc file which you opened above:

```bash
export WORKON_HOME=$HOME/.virtualenvs
export PROJECT_HOME=$HOME/Devel
source /usr/local/bin/virtualenvwrapper.sh
```

## To update shell environment

```bash
source ~/.bashrc
```

* If you face an error here, then reopen the .bashrc file by :

```bash
nano ~/.bashrc
```

## Change source from

```bash
source /usr/local/bin/virtualenvwrapper.sh
```

## to

```bash
source $HOME/.local/bin/virtualenvwrapper.sh
```

## and update shell environment by

```bash
source ~/.bashrc
```









# New virtual environment

## Make  a new virtual environment

```bash
mkvirtualenv [name of your virtual environment]
```

## To use the new virtual environment

```bash
workon [name of your virtual environment]
```

## To deactivate virtual environment
```bash
deactivate
```

## Your virtual environment is now installed




