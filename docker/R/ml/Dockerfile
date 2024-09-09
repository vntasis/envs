# syntax=docker/dockerfile:1
FROM vntasis/r-env:base-4.3.3

LABEL description="Docker image - R environment for machine learning"

# Change to root user
USER root

# Install R packages
RUN install2.r -se \
    # Modelling framework
    tidymodels \
    usemodels \
    finetune \
    multilevelmod \
    baguette \
    stacks \
    easystats \
    caret \
    #mlr3 \
    #mlr3learners \
    # Models
    xgboost \
    glmnet \
    e1071 \
    # Explainers
    DALEX \
    DALEXtra \
    # Other
    ISLR \
    bestNormalize \
    # Clean up downloaded packages
    && rm -rf /tmp/*

# Change to docker user
USER docker
