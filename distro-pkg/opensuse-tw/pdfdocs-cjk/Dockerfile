FROM opensuse/tumbleweed:latest
ARG python=python311
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
      inkscape \
      liberation-fonts \
      dejavu-fonts \
 && zypper clean --all
 
# packages for pdfdocs w/ CJK
RUN zypper refresh \
 && zypper --non-interactive install --no-recommends \
      google-noto-sans-sc-fonts \
      google-noto-sans-tc-fonts \
      google-noto-sans-kr-fonts \
      google-noto-sans-jp-fonts \
      google-noto-sans-sc-mono-fonts \
      google-noto-sans-tc-mono-fonts \
      google-noto-sans-kr-mono-fonts \
      google-noto-sans-jp-mono-fonts \
      google-noto-serif-sc-fonts \
      google-noto-serif-tc-fonts \
      google-noto-serif-kr-fonts \
      google-noto-serif-jp-fonts \
      texlive-xecjk \
 && zypper clean --all
