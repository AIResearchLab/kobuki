# Kobuki ROS2 package

This repository and the [dependencies repository](https://github.com/AIResearchLab/kobuki_dependencies.git) focuses on merging all the public forks available on the original [Kobuki Base](https://github.com/kobuki-base) repositories and extending the work towards an complete ROS2 package for kobuki based turtlebot robots.

## Installation


1. Install the following binary dependencies

    ```bash
    sudo apt install ros-humble-angles ros-humble-diagnostics ros-humble-joint-state-publisher ros-humble-ros-testing
    ```

2. Optional Dependencies for using Kobuki_keyop [Issue #21](https://github.com/ros2/teleop_twist_keyboard/issues/21)
    ```bash
    sudo apt install xterm
    ```

3. Clone main repository and dependencies
    ```bash
    git clone https://github.com/AIResearchLab/kobuki.git
    git clone https://github.com/AIResearchLab/kobuki_dependencies.git
    ```

4. Build the system with following command. 
    ```bash
    colcon build
    ```

5. Set udev rule for kobuki using following commands and unplug and replug the usb cable.
    ```bash
    wget https://raw.githubusercontent.com/kobuki-base/kobuki_ftdi/devel/60-kobuki.rules
    sudo cp 60-kobuki.rules /etc/udev/rules.d

    sudo service udev reload
    sudo service udev restart
    ```

## Non-ROS usage

### Check connectivity

Run following commands in the workspace.
```bash
source ./install/setup.bash
kobuki-version-info
```

Ouput should be like,
```bash
Version Info:
Hardware Version: 1.0.4
Firmware Version: 1.2.0
Software Version: 1.1.0
Unique Device ID: 97713968-842422349-1361404194
```

### Kobuki Teleop keyboard

Run following commands in the workspace and follow onscreen instructions
```bash
source ./install/setup.bash
kobuki-simple-keyop
```

## ROS usage

### KeyOp control

Run following commands in the workspace.
```bash
source ./install/setup.bash
ros2 launch kobuki_keyop kobuki_keyop.launch.py
```