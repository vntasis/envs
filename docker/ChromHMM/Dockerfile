FROM debian:buster-slim

LABEL maintainer "Vasilis F. Ntasis <vasilisntasis94@gmail.com>" \
        description "Docker image for ChromHMM"

# Update the system and install required libraries
RUN mkdir /usr/share/man/man1/
RUN apt-get update --fix-missing \
	&& apt-get install -y \
	default-jre \
	procps \
	unzip \
	&& apt-get clean

# Create a docker user and set home as the working directory
RUN useradd -ms /bin/bash docker
WORKDIR /home/docker
USER docker

# Install ChromHMM v1.22 Downloaded on 29/06/2021
ADD --chown=docker http://compbio.mit.edu/ChromHMM/ChromHMM.zip /home/docker/
RUN unzip /home/docker/ChromHMM
RUN rm /home/docker/ChromHMM.zip

# Run shell
CMD ["bash"]

