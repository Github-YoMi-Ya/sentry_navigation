FROM ros:eloquent

RUN mkdir -p /devkit_install
WORKDIR /devkit_install/

COPY robot_devkit ./

WORKDIR /devkit_install/robot_devkit/
RUN apt-get update --fix-missing && \
	apt-get install dialog
RUN ./demo/rdk_install.sh

CMD ["/bin/bash"]

