FROM rocker/r-ver:3.6.3

LABEL maintainer "Vasilis F. Ntasis <vasilisntasis94@gmail.com>" \
	description "Docker image environment for Matt tool (http://matt.crg.eu/)"

# Install dependencies
RUN apt-get update --fix-missing && \
        apt-get install -y \
	texlive \
	unzip \
	wget

# Copy and extract installation folder
ADD matt.tar.gz /Matt/

# Run INSTALL script
RUN cd Matt/ && ./INSTALL

# Create a symlink in the PATH for Matt
RUN ln -s /Matt/matt /bin/matt

# Create a docker user and set home as the working directory
RUN useradd -ms /bin/bash docker
WORKDIR /home/docker
USER docker


# Run
CMD ["matt"]
