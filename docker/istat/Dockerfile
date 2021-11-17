FROM debian:buster-slim

LABEL authors="Vasilis F. Ntasis <vasilisntasis94@gmail.com>" \
        description="ISTAT image - interval overlap statistics"

# Update the system and install required libraries
RUN apt-get update \
	&& apt-get install -y \
	build-essential \
	cmake \
	git \
	&& apt-get clean


# Clone istat repository
RUN git clone https://github.com/shahab-sarmashghi/ISTAT.git

# Build ISTAT
RUN cd ISTAT \
	&& mkdir build \
	&& cd build \
	&& cmake .. \
	&& make install

RUN cd / \
	&& mv ISTAT/bin/istat /usr/bin \
	&& rm -rf ISTAT

# Create a docker user and set home as the working directory
RUN useradd -ms /bin/bash docker
WORKDIR /home/docker
USER docker

# Run shell
ENTRYPOINT ["istat"]

