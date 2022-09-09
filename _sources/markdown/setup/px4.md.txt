# Environment Setup

## 1. General Dependencies

Install the general dependencies to setup all the basic things

```shell

sudo apt install -y \
    ninja-build \
    exiftool \
    python3-empy \
    python3-toml \
    python3-numpy \
    python3-yaml \
    python3-dev \
    python3-pip \
    ninja-build \
    protobuf-compiler \
    libeigen3-dev \
    genromfs \
    libignition-rendering3 \
    libgstreamer-plugins-base1.0-dev \
    gstreamer1.0-plugins-bad \
    gstreamer1.0-plugins-base \
    gstreamer1.0-plugins-good \
    gstreamer1.0-plugins-ugly

```

```shell

pip install \
    pandas \
    jinja2 \
    pyserial \
    cerberus \
    pyulog \
    numpy \
    toml \
    pyquaternion \
    kconfiglib \
    --user packaging
    --user jsonschema
```

## 2. MAVROS Installation

```shell
sudo apt install python3-catkin-tools python3-rosinstall-generator python3-osrf-pycommon -y
```

**Step 1** : Create the workspace If you haven't already

```shell
mkdir -p ~/catkin_ws/src
cd ~/catkin_ws
catkin init
wstool init src
```

**Step 2** : Install MAVLink: we use the Kinetic reference for all ROS distros as it’s not distro-specific and up to date

```shell
rosinstall_generator --rosdistro kinetic mavlink | tee /tmp/mavros.rosinstall
```

**Step 3** : Install MAVROS: get source (upstream - released)

```shell
rosinstall_generator --upstream mavros | tee -a /tmp/mavros.rosinstall
```

alternatively,

```shell
rosinstall_generator --upstream-development mavros | tee -a /tmp/mavros.rosinstall
```

**Step 4** : Create workspace and deps

```shell
wstool merge -t src /tmp/mavros.rosinstall
wstool update -t src -j4
rosdep install --from-paths src --ignore-src -y
```

**Step 5** : Install Geographiclib datasets

```shell
./src/mavros/mavros/scripts/install_geographiclib_datasets.sh
```

**Step 6** : Build source

```shell
catkin build
```

**Step 7** : Make sure to use setup.bash

```shell
source devel/setup.bash
```

## 4. PX4 Firmware Installation

```shell
cd ~/catkin_ws/src
git clone https://github.com/PX4/PX4-Autopilot.git --recursive
cd PX4-Autopilot/
make px4_sitl_default gazebo
```

Modify your .bashrc file, open it up in a text editor and add the following lines to the end

```shell

source ~/catkin_ws/devel/setup.bash
source ~/catkin_ws/src/PX4-Autopilot/Tools/setup_gazebo.bash ~/catkin_ws/src/PX4-Autopilot/ ~/catkin_ws/src/PX4-Autopilot/build/px4_sitl_default
export ROS_PACKAGE_PATH=$ROS_PACKAGE_PATH:~/catkin_ws/src/PX4-Autopilot
export ROS_PACKAGE_PATH=$ROS_PACKAGE_PATH:~/catkin_ws/src/PX4-Autopilot/Tools/sitl_gazebo

```
