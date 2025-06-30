# for htmldocs (mathjax)
ARG tag=latest
FROM fedora:$tag

RUN dnf -y update \
 && dnf install -y --setopt=tsflags=nodocs --setopt=install_weak_deps=False \
      python3-sphinx \
      python3-pyyaml \
      which \
      make \
      graphviz \
      perl-base \
      perl-File-Find \
      librsvg2-tools \
      liberation-sans-fonts \
 && dnf clean all

WORKDIR /linux
CMD bash
