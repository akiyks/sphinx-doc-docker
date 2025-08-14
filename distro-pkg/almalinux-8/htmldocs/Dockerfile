# For htmldocs
ARG tag=8
FROM almalinux:$tag

RUN dnf -y update \
 && dnf install -y --setopt=tsflags=nodocs --setopt=install_weak_deps=False \
      python3.11 \
      which \
      make \
      graphviz \
      perl-Pod-Usage \
 && dnf clean all

# install venv Sphinx
RUN cd /root \
 && python3 -m venv sphinx \
 && . sphinx/bin/activate \
 &&   pip install -U pip \
 &&   pip install Sphinx pyyaml \
 && deactivate

WORKDIR /linux
CMD bash
