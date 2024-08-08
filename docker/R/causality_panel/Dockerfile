# syntax=docker/dockerfile:1
FROM vntasis/r-env:base-4.3.3

LABEL description="Docker image for R environment for causality inference with panel data"

# Change to root user
USER root

# Install R packages
RUN install2.r -se \
    latex2exp \
    PanelMatch \
    && installGithub.r \
    synth-inference/synthdid \
    bcallaway11/ife \
    susanathey/MCPanel \
    chadhazlett/KBAL \
    xuyiqing/tjbal \
    xuyiqing/fect \
    xuyiqing/panelView \
    # Clean up downloaded packages
    && rm -rf /tmp/*


# Change to docker user
USER docker
