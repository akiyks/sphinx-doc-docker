# For htmldocs
ARG tag=10
FROM almalinux:$tag

RUN dnf -y update \
 && dnf install -y 'dnf-command(config-manager)' \
 && dnf config-manager --set-enabled crb \
 && dnf install -y --setopt=tsflags=nodocs --setopt=install_weak_deps=False \
     --enablerepo=crb \
      python3-sphinx \
      python3-pyyaml \
      which \
      make \
      graphviz \
      perl \
 && dnf clean all

WORKDIR /linux
CMD bash

# For pdfdocs (non-CJK)
# EPEL 10 doesn't have Inkscape.  Install rsvg-convert and ImageMagick here.

RUN dnf -y update \
 && dnf install -y epel-release \
 && dnf install -y almalinux-release-devel \
 && dnf -y update \
 && dnf install -y --setopt=tsflags=nodocs --setopt=install_weak_deps=False \
      python3-sphinx-latex \
      latexmk \
      texlive-xetex \
      dejavu-fonts-all \
      liberation-sans-fonts \
      librsvg2-tools \
      ImageMagick \
 && dnf clean all
COPY 09-texlive-fonts.conf /etc/fonts/conf.d/
RUN fc-cache -sf
