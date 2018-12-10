FROM amazonlinux:1

RUN yum install -y python36 python36-pip make gcc python36-devel
RUN python3 -m pip install awscli

ARG GIT_REVISION=unknown
ARG GIT_ORIGIN=unknown
ARG IMAGE_NAME=unknown
LABEL git-revision=$GIT_REVISION \
      git-origin=$GIT_ORIGIN \
      image-name=$IMAGE_NAME
