# June 2024
# Joaquín A. Vásquez

# Import ros humble
FROM ros:humble-ros-base-jammy

# Set bash as default shell
SHELL ["/bin/bash", "-c"]

# Arguments
ARG ROS_DISTRO=humble

####### MIRCROROS INSTALLATION #######
# Create a workspace and download the micro-ROS tools
WORKDIR /home/microros_ws
RUN git clone -b $ROS_DISTRO https://github.com/micro-ROS/micro_ros_setup.git src/micro_ros_setup

# Update dependencies using rosdep
RUN apt update && rosdep update
RUN rosdep install --from-paths src --ignore-src -y

# Install pip
RUN apt-get install python3-pip -y

# Source the ROS 2 installation && 
# Build micro-ROS tools and source them
RUN source /opt/ros/$ROS_DISTRO/setup.bash && \
    colcon build
####### MIRCRO-ROS INSTALLATION ########

########### MIRCRO-ROS SETUP ###########
RUN source /opt/ros/$ROS_DISTRO/setup.bash && \
    source install/local_setup.bash && \
    ros2 run micro_ros_setup create_firmware_ws.sh host
########### MIRCRO-ROS SETUP ###########

# Source for our all terminals
RUN echo "source /opt/ros/$ROS_DISTRO/setup.bash" >> ~/.bashrc
RUN echo "source /home/microros_ws/install/local_setup.bash" >> ~/.bashrc