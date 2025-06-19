# for epubdocs and pdfdocs (no CJK)
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

RUN dnf -y update \
 && dnf install -y --setopt=tsflags=nodocs --setopt=install_weak_deps=False \
      python3-sphinx-latex \
      latexmk \
      texlive-xetex \
      texlive-ellipse \
      texlive-pict2e \
      texlive-fontawesome5 \
      dejavu-fonts-all \
      inkscape \
 && dnf clean all
COPY 09-texlive-fonts.conf /etc/fonts/conf.d/
RUN fc-cache -sf
