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
# EPEL 10 doesn't have Inkscape.  Install rsvg-convert and ImageMagick here.

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
      librsvg2-tools \
      ImageMagick \
      poppler-utils \
 && dnf clean all
COPY 09-texlive-fonts.conf /etc/fonts/conf.d/
RUN fc-cache -sf

# For pdfdocs with CJK

RUN dnf -y update \
 && dnf install -y --setopt=tsflags=nodocs --setopt=install_weak_deps=False \
      texlive-ctex \
 && dnf clean all

# We need to download static noto CJK fonts from google fonts site.

RUN cd /opt \
 && curl https://github.com/googlefonts/noto-cjk/releases/download/Serif2.003/04_NotoSerifCJKOTC.zip -L -O \
 && curl https://github.com/googlefonts/noto-cjk/releases/download/Sans2.004/03_NotoSansCJK-OTC.zip -L -O \
 && unzip 04_NotoSerifCJKOTC.zip \
 && rm LICENSE \
 && unzip 03_NotoSansCJK-OTC.zip \
 && mkdir /usr/local/share/fonts/ \
 && mv OTC/NotoSerifCJK-Bold.ttc OTC/NotoSerifCJK-Regular.ttc /usr/local/share/fonts/ \
 && mv NotoSansCJK-Bold.ttc NotoSansCJK-Regular.ttc /usr/local/share/fonts/ \
 && mv LICENSE /usr/local/share/fonts/ \
 && rm -r * \
 && fc-cache -f /usr/local/share/fonts

COPY fonts.conf /root/deny-vf/fontconfig/fonts.conf
