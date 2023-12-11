FROM opensuse/leap:latest
ARG sphinx_pkg=python3-Sphinx_4_2_0
# packages for htmldocs, (latexdocs is not covered)
RUN zypper refresh \
 && zypper --non-interactive install --no-recommends \
      $sphinx_pkg \
      python3-PyYAML \
      perl \
      which \
      make \
      graphviz \
 && zypper clean --all

WORKDIR /linux
CMD bash
