# Installation of virtualenvwrapper, OpenCV and cv_bridge package  : 

## Installation of virtualenvwrapper

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

<br><br>


# Installation of opencv

```bash
pip install opencv-python
```

## Open Python interpreter in terminal by :

```bash
python
```

## Import opencv in the above open Python interpreter

```python
import cv2
```

## If your import statement executes error-free, you are good to go 

<br><br>



# Installation of cv-bridge

## Open your terminal and write : 

```bash
sudo apt-get install ros-noetic-cv-bridge
```

## To check if cv_bridge is installed


### Note : cv_bridge is a ros package, so make sure you source your ROS before running the command below

```bash
rospack find cv_bridge
```



