FROM rocker/r-ver:4.0.4

LABEL maintainer "Vasilis F. Ntasis <vasilisntasis94@gmail.com>" \
	description "Docker image for R environment for bayesian modelling"

# Install dependencies
RUN apt-get update --fix-missing \
        && apt-get install -y \
	less \
	libxml2-dev \
	libnode-dev \
	libglpk-dev \
	# X11 dependencies
	libsm-dev \
	libxt-dev \
	# Clean up
	&& apt-get autoremove \
	&& apt-get clean

# Install R packages
# rstanarm imports rstan, bayesplot, loo
# tidybayes imports coda
RUN install2.r \
	rstanarm \
	tidyposterior \
	tidybayes \
	remotes \
	&& r -e 'remotes::install_github("stan-dev/posterior")'

# Create a docker user and set home as the working directory
RUN useradd -ms /bin/bash docker
WORKDIR /home/docker
USER docker


# Run R
CMD ["R"]
