FROM rocker/r-ver:3.6.3

LABEL maintainer "Vasilis F. Ntasis <vasilisntasis94@gmail.com>" \
	description "Docker image for R environment"

# Install dependencies
RUN apt-get update --fix-missing && \
        apt-get install -y \
	libz-dev \
	libssl-dev \
	libcurl4-openssl-dev \
	libxml2-dev \
	libgsl-dev \
	cargo \
	libpng-dev \
	libjpeg-dev \
	libbz2-dev \
	liblzma-dev

# Install R packages
#RUN R -e 'install.packages("littler")'
RUN install2.r \
	tidyverse \
	vroom \
	caret \
	gplots \
	BiocManager \
	#rmarkdown \ already installed
	gprofiler2 \
	feather \
	#data.table \ already installed
	gganimate \
	gifski \
	ggplotify \
	devtools \
	#paleteer \ not compatible with version 3.6.3
	ggsci \
	ggupset \
	#tweenr \ already installed
        workflowr \
        seriation \
        tidybayes \
        ggridges \
        #rstudio \
        ggpubr \
        #ggsignif \ already installed
        mlr3 \
        #modelr \ already installed
        ggstatsplot \
        Rfast \
        gifski \
        ggfortify \
        Rtsne \
        #scatterplot3d \ not compatible with version 3.6.3
        gt \
        tidyposterior \
        rstan \
        ggmcmc \
        loo \
        coda \
        bayesplot \
	sjstats \
	heatmaply
	#lpSolve

# Install Bioconductor packages
RUN Rscript -e "BiocManager::install(c('edgeR','limma','DESeq2','ComplexHeatmap','clusterProfiler','Sushi','genomation','fgsea'))"

RUN install2.r \
 	# needs IRanges from bioconductor
	tidygenomics \
	# requires ComplexHeatmap
	tidyHeatmap


# X11 dependencies
RUN apt-get install -y \
	libsm-dev \
	libxt-dev

# Add here more packages
RUN install2.r \
	restriktor \
	idr

# Create a docker user and set home as the working directory
RUN useradd -ms /bin/bash docker
WORKDIR /home/docker
USER docker


# Run R
CMD ["R"]
