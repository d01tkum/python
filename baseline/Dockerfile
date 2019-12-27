FROM continuumio/anaconda3:5.3.0
MAINTAINER d01tkum

# Add user
ENV USER=d01tkum
ENV HOME=/home/${USER}
ENV SHELL /bin/bash

RUN useradd -m ${USER}
 && gpasswd -a ${USER} sudo
 && echo "${USER}:hoge" | chpasswd
 && su ${USER}

RUN apt update -qq \
 && apt upgrade -y \
 && apt install --no-install-recommends -y libgtk2.0-0 \
 && apt clean \
 && rm -rf /var/lib/apt/lists/*

ENV NOTEBOOK_DIR=/src/Workspace \
	NOTEBOOK_IP=0.0.0.0 \
	NOTEBOOK_PORT=8888

RUN conda install -y --quiet \
	jupyter \
	Pillow \
 && conda config --add channels conda-forge \
 && conda clean -tipsy

CMD jupyter lab \
	--notebook-dir=${NOTEBOOK_DIR} \
	--ip=${NOTEBOOK_IP} \
	--port=${NOTEBOOK_PORT} \
	--NotebookApp.token='' \
	--no-browser \
	--allow-root

