# syntax=docker/dockerfile:1
FROM rocker/r-ver:4.3.3

LABEL authors="Vasilis F. Ntasis <vasilisntasis94@gmail.com>" \
    description="Docker base image for R environment"

# Install dependencies
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    # useful for viewing help pages
    less \
    # required by gganimate
    libcairo2-dev \
    # image rendering
    libjpeg-dev \
    libpng-dev \
    # X11 dependencies
    libsm-dev \
    libxt-dev \
    # required by gg3D
    libtcl8.6 \
    libtk8.6 \
    # required by tidyverse
    libxml2-dev \
    # for rendering reports
    pandoc \
    # Clean up
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Install R packages
RUN install2.r -se \
    bench \
    devtools \
    dslabs \
    fakir \
    furrr \
    GGally \
    gganimate \
    ggforce \
    ggfortify \
    ggplotify \
    ggpointdensity \
    ggpubr \
    ggridges \
    ggside \
    ggsignif \
    ggstatsplot \
    ggupset \
    gifski \
    lobstr \
    pheatmap \
    Rtsne \
    seriation \
    sjstats \
    tidyverse \
    vroom \
    # Color Palettes
    ggsci \
    ggthemes \
    nord \
    paletteer \
    pals \
    Polychrome \
    viridis \
    wesanderson \
    # Install packages from github
    && installGithub.r \
    AckerDWM/gg3D \
    BlakeRMills/MetBrewer \
    jaredhuling/jcolors \
    johannesbjork/LaCroixColoR \
    thomasp85/patchwork \
    thomasp85/scico \
    # Clean up downloaded packages
    && rm -rf /tmp/*

# Create a docker user and set home as the working directory
RUN useradd -ms /bin/bash docker
WORKDIR /home/docker
USER docker


# Run R
CMD ["R"]
