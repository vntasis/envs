FROM vntasis/r-env:small

LABEL authors="Vasilis F. Ntasis <vasilisntasis94@gmail.com>" \
	description="Docker image - R environment for machine learning"

# Change to root user
USER root

# Install dependencies
RUN apt-get update && \
	apt-get install -y \
	libomp-dev \
	&& apt-get clean


# Install R packages
RUN install2.r \
	ISLR \
	xgboost \
	glmnet \
	DALEX \
	DALEXtra \
	mlr3 \
	mlr3learners \
	caret \
	e1071 \
	doParallel


# Clean up downloaded packages
RUN rm -r /tmp/downloaded_packages/

# Change to docker user
USER docker
