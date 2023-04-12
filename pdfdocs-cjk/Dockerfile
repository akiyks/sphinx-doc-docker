# Derived from sphinx-doc/docker/latexpdf/Dockerfile.
# Covers epubdocs and pdfdocs (CJK).
# use "/linux" as WORKDIR
# use "bash" as CMD
FROM python:slim
LABEL maintainer="Akira Yokosawa <akiyks@gmail.com>"
WORKDIR /linux

# Packages covering htmldocs (mathjax) and latexdocs
RUN apt-get update \
 && apt-get upgrade -y \
 && apt-get install --no-install-recommends -y \
      graphviz \
      inkscape \
      make \
      perl \
      fonts-liberation \      
 && apt-get autoremove -y \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/*

RUN python3 -m pip install --no-cache-dir -U pip
ARG sphinxrel=6.1.3
RUN python3 -m pip install --no-cache-dir Sphinx==$sphinxrel Pillow

CMD bash

#--- Cut here if all you need are htmldocs (mathjax) and latexdocs ---
# Packages covering htmldocs (imgmath), epubdocs, and non-CJK pdfdocs
RUN apt-get update \
 && apt-get install --no-install-recommends -y \
      latexmk \
      lmodern \
      tex-gyre \
      fonts-dejavu \
      texlive-fonts-recommended \
      texlive-latex-extra \
      texlive-xetex \
      tex-common \
      dvipng \
      dvisvgm \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/*

#--- Cut here if you don't need CJK pdfdocs ---
# Packages covering CJK pdfdocs
RUN apt-get update \
 && apt-get install --no-install-recommends -y \
      fonts-noto-cjk \
      texlive-lang-chinese \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/*
