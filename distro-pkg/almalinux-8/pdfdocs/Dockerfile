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

# for pdfdocs (w/o CJK)
RUN dnf install -y epel-release \
 && dnf install -y --setopt=tsflags=nodocs --setopt=install_weak_deps=False \
      inkscape \
      dejavu-sans-fonts \
      dejavu-sans-mono-fonts \
      dejavu-serif-fonts \
      latexmk \
      librsvg2-tools \
      texlive-amscls \
      texlive-amsfonts \
      texlive-amsmath \
      texlive-anyfontsize \
      texlive-capt-of \
      texlive-cmap \
      texlive-collection-fontsrecommended \
      texlive-collection-latex \
      texlive-ec \
      texlive-eqparbox \
      texlive-euenc \
      texlive-fancybox \
      texlive-fancyvrb \
      texlive-float \
      texlive-fncychap \
      texlive-framed \
      texlive-luatex85 \
      texlive-mdwtools \
      texlive-multirow \
      texlive-needspace \
      texlive-oberdiek \
      texlive-parskip \
      texlive-polyglossia \
      texlive-psnfss \
      texlive-tabulary \
      texlive-threeparttable \
      texlive-titlesec \
      texlive-tools \
      texlive-ucs \
      texlive-upquote \
      texlive-wrapfig \
      texlive-xetex \
 && dnf clean all \
 && ln -sf /usr/bin/python3.11 /etc/alternatives/python3 \
 && mktexfmt xelatex.fmt
 