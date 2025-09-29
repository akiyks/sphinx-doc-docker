FROM opensuse/leap:16.0
ARG python=python3
ENV LANG=C.UTF-8 LC_ALL=C.UTF-8
# packages for htmldocs (mathjax)
RUN zypper refresh \
 && zypper --non-interactive install --no-recommends \
      $python-Sphinx \
      $python-PyYAML \
      perl \
      which \
      make \
      graphviz \
 && zypper clean --all

WORKDIR /linux
CMD bash

# packages for htmldocs (imgmath), pdfdocs (w/o CJK)
RUN zypper refresh \
 && zypper --non-interactive install --no-recommends \
      $python-Sphinx-latex \
      texlive-xetex \
      texlive-dvisvgm \
      texlive-ellipse \
      texlive-pict2e \
      inkscape \
      liberation-fonts \
      dejavu-fonts \
      poppler-tools \
 && zypper clean --all
