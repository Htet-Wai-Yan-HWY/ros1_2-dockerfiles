FROM tiryoh/ros-desktop-vnc:noetic
LABEL maintainer="htetwaiyan.zyme@gmail.com"


ARG USERNAME=ubuntu
ARG USER_UID=1000
ARG USER_GID=$USER_UID

ARG ROS_DISTRO=noetic


RUN wget -q -O - https://dl.google.com/linux/linux_signing_key.pub | apt-key add -


RUN apt-get update && apt-get install -y nano && rm -rf /var/lib/apt/lists/*


# RUN  mkdir /home/$USERNAME/.config && chown $USER_UID:$USER_GID /home/$USERNAME/.config
    
RUN usermod -aG sudo ${USERNAME}

RUN apt install curl \
    && curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -

COPY ./ros-noetic-desktop.sh /ros-noetic-desktop.sh


COPY entrypoint.sh /entrypoint.sh

RUN sudo chmod 777 /ros-noetic-desktop.sh
RUN sudo chmod 777 /entrypoint.sh
# RUN touch /etc/sudoers.d/$USERNAME
# RUN echo $USERNAMEmALL=\(root\) NOPASSSWORD:ALL > /etc/sudoers.d/$USERNAME \
#     && chmod 0440 /etc/sudoers.d/$USERNAME 

ENTRYPOINT [ "/entrypoint.sh" ]

# ENTRYPOINT [ "/ros-noetic-desktop.sh" ]

CMD ["bash"]