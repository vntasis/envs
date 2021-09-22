FROM rocker/r-ver:4.0.4

LABEL maintainer "Vasilis F. Ntasis <vasilisntasis94@gmail.com>" \
	description "Docker image for R environment"

# Install dependencies
RUN apt-get update --fix-missing && \
        apt-get install -y \
	less \
	libz-dev \
	libssl-dev \
	libcurl4-openssl-dev \
	libxml2-dev \
	libgsl-dev \
	cargo \
	libpng-dev \
	libjpeg-dev \
	libbz2-dev \
	liblzma-dev \
	libcairo2-dev \
	libglpk-dev \
# X11 dependencies
	libsm-dev \
	libxt-dev

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
	paletteer \
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
RUN Rscript -e "devtools::install_github('stemangiola/tidyHeatmap')"

RUN install2.r \
 	# needs IRanges from bioconductor
	tidygenomics
	# requires ComplexHeatmap
	#tidyHeatmap


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
