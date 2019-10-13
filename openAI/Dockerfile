FROM d01tkum/dockerfile_python:baseline

RUN apt update -qq \
 && apt upgrade -y\
 && apt install -y --no-install-recommends -y \
 	# opencv3
	libgtk2.0-0 \
 && apt clean \
 && rm -rf /var/lib/apt/lists/*

RUN pip install gym \
 && pip install 'gym[atari]' \
 && pip install 'gym[all]'
