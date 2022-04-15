# For installation of virtual environment wrapper and creating a virtual enviornment : 

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

## New virtual environment

## Make  a new virtual environment

```bash
mkvirtualenv [name of your virtual environment]
```

## To use the new virtual environment

```bash
workon [name of your virtual environment]
```

## Your virtual environment is now up and running, now we will install opencv in the virtual environment you just created

## Installation of opencv

```bash
pip install opencv-python
```

## Open Python interpreter in terminal

```bash
python
```

## import opencv in the above open Python interpreter

```python
import cv2
```

## Your virtual environment and opencv are installed and good to go 

## Installation of cv-bridge

```bash
sudo apt-get install ros-noetic-cv-bridge
```

## To check if cv_bridge is installed

### Note : cv_bridge is a ros package, so make sure you source your ROS before running the command below

```bash
rospack find cv_bridge
```