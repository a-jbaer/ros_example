FROM osrf/ros:humble-desktop-full

ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=$USER_UID

# Create the user
RUN groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -ms /bin/bash $USERNAME \
    #
    # [Optional] Add sudo support. Omit if you don't need to install software after connecting.
    && apt-get update \
    && apt-get install -y sudo \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME

RUN groupmod --gid $USER_GID $USERNAME \
    && usermod --uid $USER_UID --gid $USER_GID $USERNAME \
    && chown -R $USER_UID:$USER_GID /home/$USERNAME

RUN apt update && apt -y full-upgrade

############################

RUN apt-get update
RUN apt-get install -y git 
RUN apt-get install -y vim
RUN apt-get install -y python3-pip

# RUN echo "source /opt/ros/melodic/setup.bash" >> /root/.bashrc

# RUN mkdir -p ~/catkin_ws/src && cd ~/catkin_ws/src
# RUN /bin/bash -c '. /opt/ros/melodic/setup.bash; catkin_init_workspace ~/catkin_ws/src'
# RUN /bin/bash -c '. /opt/ros/melodic/setup.bash; cd ~/catkin_ws; catkin_make'

# RUN /bin/bash -c '. /opt/ros/melodic/setup.bash; cd ~/catkin_ws; catkin_create_pkg learning_tf tf roscpp rospy turtlesim'
# RUN /bin/bash -c '. /opt/ros/melodic/setup.bash; cd ~/catkin_ws; catkin_make'


RUN echo "ALL DONE !"

############################

RUN apt -y install x11-apps

ENV DISPLAY=:0
ENV PULSE_SERVER=/tmp/PulseServer

