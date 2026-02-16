## Robot Package Template

This is a GitHub template. You can make your own copy by clicking the green "Use this template" button.

It is recommended that you keep the repo/package name the same, but if you do change it, ensure you do a "Find all" using your IDE (or the built-in GitHub IDE by hitting the `.` key) and rename all instances of `my_bot` to whatever your project's name is.

Note that each directory currently has at least one file in it to ensure that git tracks the files (and, consequently, that a fresh clone has direcctories present for CMake to find). These example files can be removed if required (and the directories can be removed if `CMakeLists.txt` is adjusted accordingly).


Install docker use given image to create a container

Link your current directory with container and create a container using:
    
docker run -it --rm \
  --name irrp_ros \
  --net=host \
  --ipc=host \
  -v /home/sha/Documents/IRRP/Project/Object-Fetching-via-Waypoint-Navigation:/home/ros/ws \
  irrp-humble

xhost +local:docker

docker run -it --rm \
  --name irrp_ros2 \
  --net=host \
  --ipc=host \
  -e DISPLAY=$DISPLAY \
  -v /tmp/.X11-unix:/tmp/.X11-unix \
  -v /home/sha/Documents/IRRP/Project/dev_ws:/home/ros/ws \
  irrp-humble


// for gazebo environemnt usage of gpu
xhost +local:docker

docker run -it --rm \
  --name irrp_ros2 \
  --net=host \
  --ipc=host \
  --gpus all \
  -e DISPLAY=$DISPLAY \
  -e QT_X11_NO_MITSHM=1 \
  -e NVIDIA_VISIBLE_DEVICES=all \
  -e NVIDIA_DRIVER_CAPABILITIES=all \
  -v /tmp/.X11-unix:/tmp/.X11-unix \
  -v /home/sha/Documents/IRRP/Project/dev_ws:/home/ros/ws \
  irrp-humble
  
docker exec -it irrp_ros2 bash

source install/setup.bash

ros2 launch my_bot rsp.launch.py


// runt this to create new terminal always
docker ps -> reveals all the docker containers running

// to rebuild the current package
 colcon build --symlink-install


//inside container always run this
source /opt/ros/humble/setup.bash
source ~/ws/install/setup.bash

//lauches the links
ros2 launch my_bot rsp.launch.py

//to run rviz
rviz2

//to run saved rviz
rviz2 -d path

// launches the wheels
ros2 run joint_state_publisher_gui joint_state_publisher_gui


//to launch gazebo
ros2 launch gazebo_ros gazebo.launch.py 

// to spawn the robot Description
ros2 run gazebo_ros spawn_entity.py -topic robot_description -entity bot

// one command to start gazebo 
ros2 launch my_bot launch_sim.launch.py


// we use ros2_control commands to run this in gazebo environemnt

//to run controls
ros2 run teleop_twist_keyboard  teleop_twist_keyboard