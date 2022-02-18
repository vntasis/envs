FROM rocker/r-ver:4.0.4

LABEL authors="Vasilis F. Ntasis <vasilisntasis94@gmail.com>" \
	description="Docker small image for R environment"

# Install dependencies
RUN apt-get update && \
        apt-get install -y \
	# useful for viewing help pages
	less \
	#
	libpng-dev \
	libjpeg-dev \
	# required by gganimate
	libcairo2-dev \
	# required by tidyverse
	libxml2-dev \
	# required by gg3D
	libtcl8.6 \
	libtk8.6 \
	#
	#libz-dev \
	#libssl-dev \
	#libcurl4-openssl-dev \
	#libgsl-dev \
	#cargo \
	#libbz2-dev \
	#liblzma-dev \
	#libglpk-dev \
	# X11 dependencies
	libsm-dev \
	libxt-dev \
	# Clean up
	&& apt-get clean

# Install R packages
RUN install2.r \
	tidyverse \
	vroom \
	devtools \
	paletteer \
	ggstatsplot \
	ggpubr \
	ggsignif \
	ggfortify \
	gganimate \
	gifski \
	ggplotify \
	ggupset \
	ggridges \
	ggpointdensity \
	Rtsne \
	sjstats \
	restriktor \
	dslabs

# Install packages from github
RUN r -e 'devtools::install_github(c("AckerDWM/gg3D","thomasp85/patchwork"))'

# Clean up downloaded packages
RUN rm -r /tmp/downloaded_packages/

# Create a docker user and set home as the working directory
RUN useradd -ms /bin/bash docker
WORKDIR /home/docker
USER docker


# Run R
CMD ["R"]
