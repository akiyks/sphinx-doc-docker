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

