# UFACTORY XARM UF850 ROBOTIC ARM

This repository is a walk through on the basic of Robotic Operating System (ROS2). ROS Integration happens to be a fore front runner of major robotic integration in the industry. In the resository, the idea of **Unified Robot Description Format(URDF)**, in simple term: taking all mechanical parts of a robot and putting them together, as well as the visualizing of the coupled system using **RVizz2** in a computer is introduced. 

---

## Setup Instruction

### 1. **Install ROS2** 
Specifically Jazzy. Since the version I used was jazzy, but any other version is okay. Only that there will be need for some debugging. You can install it by going through the ROS documentatation.

### 2. **Launch file** 
This can be wriiten manually but you can get access to one by just running the following command

```bash
    sudo apt install ros-jazzy-urdf-tutorial
```
or you can clone from the following github

```bash
    git clone https://github.com/ros/urdf_tutorial.git
```

### 3. **Create a ROS2 Workspace and PACKAGE** 
To do this first create a folder name **uf850_ws** in your desired directory, the run the command
```bash
    ros2 pkg create --build-type ament-cmake uf850_description
```

**uf850** - ROS2 Workspace /n
**uf850_description** - ROS2 package

### 4. Clone the respository
Inside the package folder **ut850_description**, run the command in the terminal
```bash
    git clone git@github.com:Chukwuebuka-favour/Ufactory-xarm-uf850-Robotic-Arm.git
```

### 5. **Colcon build**

Build the package
```bash
    colcon build
```
Then source the setup file
```bash
    source install/setup.bash
```

### 6. Format the CMakeLists.txt
After you ran the cmd for creating you workspace and package a file **CMakeLists.txt** was added to yor package. You need to add the following snippet just between **endif()** and **ament_package()** to ensure you don't run into any issue while lauching the package.

The snippet is as follows

```bash
    endif()

    INSTALL (DIRECTORY meshes urdf
    DESTINATION share/${PROJECT_NAME}/
    )

    ament_package()

```

### 7. Lauch the package in RViz2
Run the command in your terminal, with the current directory the workspace created **uf850_ws**
```bash
ros2 launch urdf_tutorial display.launch.py model:=$PWD/uf850_description/urdf/uf850.urdf
```
