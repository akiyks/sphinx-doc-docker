# For htmldocs
ARG tag=latest
FROM almalinux:$tag

RUN dnf -y update \
 && dnf install -y 'dnf-command(config-manager)' \
 && dnf config-manager --set-enabled crb \
 && dnf install -y --setopt=tsflags=nodocs --setopt=install_weak_deps=False \
     --enablerepo=crb \
      python3-sphinx \
      python3-pyyaml \
      which \
      make \
      graphviz \
      perl-base \
      perl-File-Find \
      librsvg2-tools \
      liberation-sans-fonts \
 && dnf clean all

WORKDIR /linux
CMD bash
