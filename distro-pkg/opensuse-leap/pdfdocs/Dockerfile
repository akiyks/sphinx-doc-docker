FROM opensuse/leap:latest
ARG sphinx_pkg=python3-Sphinx_4_2_0
# packages for htmldocs, (latexdocs is not covered)
RUN zypper refresh \
 && zypper --non-interactive install --no-recommends \
      $sphinx_pkg \
      perl \
      which \
      make \
      graphviz \
 && zypper clean --all

WORKDIR /linux
CMD bash

# Additional packages for latexdocs, epubdocs, and pdfdocs (no-CJK)
RUN zypper refresh \
 && zypper --non-interactive install --no-recommends \
      $sphinx_pkg-latex \
      inkscape \
      texlive-tex-gyre \
      texlive-xetex \
      dejavu-fonts \
 && zypper clean --all
