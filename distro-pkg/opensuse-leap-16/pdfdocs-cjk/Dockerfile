FROM opensuse/leap:16.0
ARG python=python3
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
 && zypper clean --all

WORKDIR /linux
CMD bash

# packages for htmldocs (imgmath), pdfdocs (w/o CJK)
RUN zypper refresh \
 && zypper --non-interactive install --no-recommends \
      $python-Sphinx-latex \
      texlive-xetex \
      texlive-dvisvgm \
      texlive-ellipse \
      texlive-pict2e \
      inkscape \
      liberation-fonts \
      dejavu-fonts \
      poppler-tools \
 && zypper clean --all
 
# packages for pdfdocs w/ CJK
RUN zypper refresh \
 && zypper --non-interactive install --no-recommends \
      texlive-xecjk \
      unzip \
 && zypper clean --all
# openSUSE tumbleweed has replaced static Noto CJK fonts with variable ones,
# which are not compatible with xelatex.
# We need to download static ones from google fonts site.
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
