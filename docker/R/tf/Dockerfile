FROM vntasis/r-env:small

LABEL authors="Vasilis F. Ntasis <vasilisntasis94@gmail.com>" \
	description="Docker image - R environment for Transcription Factor analysis"

# Change to root user
USER root

# Update and install any dependencies
RUN apt-get update && \
	apt-get install -y \
	libglpk-dev \
	&& apt-get clean


# Install R packages
RUN install2.r BiocManager

# Install Bioconductor packages
RUN r -e "BiocManager::install('saezlab/decoupleR', dependencies = TRUE)"

# Clean up downloaded packages
RUN rm -r /tmp/downloaded_packages/

# Change to docker user
USER docker

