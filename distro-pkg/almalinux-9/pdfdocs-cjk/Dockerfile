# For htmldocs
ARG tag=latest
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
      perl-base \
      perl-File-Find \
      librsvg2-tools \
      liberation-sans-fonts \
 && dnf clean all

WORKDIR /linux
CMD bash

# For pdfdocs (non-CJK)

RUN dnf -y update \
 && dnf install -y epel-release \
 && dnf install -y almalinux-release-devel \
 && dnf -y update \
 && dnf install -y --setopt=tsflags=nodocs --setopt=install_weak_deps=False \
      python3-sphinx-latex \
      latexmk \
      texlive-xetex \
      dejavu-fonts-all \
      inkscape \
 && dnf clean all
COPY 09-texlive-fonts.conf /etc/fonts/conf.d/
RUN fc-cache -sf

# For pdfdocs with CJK

RUN dnf -y update \
 && dnf install -y --setopt=tsflags=nodocs --setopt=install_weak_deps=False \
      texlive-xecjk \
      texlive-ctex \
      google-noto-serif-cjk-ttc-fonts \
      google-noto-sans-cjk-ttc-fonts \
 && dnf clean all
