# For htmldocs
ARG tag=10
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
      perl \
 && dnf clean all

WORKDIR /linux
CMD bash

# For pdfdocs (non-CJK)

RUN dnf -y update \
 && dnf install -y epel-release \
 && dnf install -y almalinux-release-devel \
 && dnf -y update \
 && dnf install -y --setopt=tsflags=nodocs --setopt=install_weak_deps=False \
      python3-sphinx-latex \
      latexmk \
      texlive-xetex \
      dejavu-fonts-all \
      liberation-sans-fonts \
 && dnf clean all
COPY 09-texlive-fonts.conf /etc/fonts/conf.d/
RUN fc-cache -sf

# Install inkscape from flathub
RUN dnf -y update \
 && dnf install -y --setopt=tsflags=nodocs --setopt=install_weak_deps=False \
      flatpak \
      flatpak-xdg-utils \
      librsvg2-tools \
 && dnf clean all \
 && flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo \
 && flatpak install -y flathub org.gnome.Platform/x86_64/48 \
 && flatpak install -y flathub org.inkscape.Inkscape

COPY inkscape-sh /usr/local/bin/inkscape
RUN chmod +x /usr/local/bin/inkscape
