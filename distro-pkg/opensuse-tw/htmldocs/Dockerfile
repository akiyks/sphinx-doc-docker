FROM opensuse/tumbleweed:latest
ARG python=python311
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
      rsvg-convert \
 && zypper clean --all

WORKDIR /linux
CMD bash
