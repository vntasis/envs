# syntax=docker/dockerfile:1
FROM vntasis/r-env:base-4.3.3

LABEL maintainer "Vasilis F. Ntasis <vasilisntasis94@gmail.com>" \
    description "Docker image for R general bioinformatics environment"

# Change to root user
USER root

# Install dependencies
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    # igraph dep
    libglpk-dev \
    # Rhtslib deps
    libbz2-dev \
    libcurl4-openssl-dev \
    liblzma-dev \
    # Clean up
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Install R packages
RUN install2.r -se \
    BiocManager \
    CMplot \
    ggseqlogo \
    gprofiler2 \
    gt \
    idr \
    # Install Bioconductor packages
    && r -e 'BiocManager::install(\
    c(\
        "clusterProfiler", \
        "ComplexHeatmap", \
        "DESeq2", \
        "edgeR", \
        "genomation", \
        "ggbio", \
        "karyoploteR", \
        "limma", \
        "plotgardener", \
        "sva", \
        "tidybulk", \
        "tidySummarizedExperiment", \
        "variancePartition", \
        "vsn" \
    ), update = TRUE, ask = FALSE)' \
    # Install packages from github
    && installGithub.r \
    jeffsocal/tidyproteomics \
    stemangiola/tidyHeatmap \
    thomasp85/tidygraph \
    # Clean up downloaded packages
    && rm -rf /tmp/*

# Change to docker user
USER docker
