# for htmldocs (using pythonvenv)
FROM almalinux:8

ENV LC_ALL=C.UTF-8
ENV LANG=C.UTF-8
ENV LANGUAGE=C.UTF-8

RUN dnf -y update \
 && dnf install -y --setopt=tsflags=nodocs \
      python312 \
      which \
      make \
      graphviz \
      perl \
 && dnf clean all

WORKDIR /root
RUN python3.12 -m venv sphinx-venv \
 && source sphinx-venv/bin/activate \
 && pip install -U pip \
 && pip install Sphinx sphinx_rtd_theme pyyaml \
 && deactivate

WORKDIR /linux
CMD /bin/bash
