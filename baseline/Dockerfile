FROM continuumio/anaconda3:5.3.0
MAINTAINER d01tkum

ENV DEBIAN_FRONTEND noninteractive
RUN apt update -qq \
 && apt upgrade -y \
 && apt install --no-install-recommends -y \
	# opencv3
	libgtk2.0-0 \
 && apt clean \
 && rm -rf /var/lib/apt/lists/*

ENV NOTEBOOK_DIR=/src/workspace \
	NOTEBOOK_IP=0.0.0.0 \
	NOTEBOOK_PORT=8888

RUN conda install -y --quiet \
	jupyter \
	Pillow \
 && conda config --add channels conda-forge \
	# opencv3 install
 && conda install -c menpo opencv3 \
 && conda clean -tipsy

CMD jupyter lab \
	--notebook-dir=${NOTEBOOK_DIR} \
	--ip=${NOTEBOOK_IP} \
	--port=${NOTEBOOK_PORT} \
	--NotebookApp.token='' \
	--no-browser \
	--allow-root

