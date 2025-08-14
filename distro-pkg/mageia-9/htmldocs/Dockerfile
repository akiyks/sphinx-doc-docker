# for htmldocs
FROM mageia:9

RUN dnf update -y \
 && dnf install -y --setopt=tsflags=nodocs --setopt=install_weak_deps=False \
      make \
      graphviz \
      python3-yaml \
      python3-sphinx \
 && dnf clean all

WORKDIR /linux
CMD bash
