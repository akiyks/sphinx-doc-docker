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
 && curl https://github.com/googlefonts/noto-cjk/raw/main/Sans/SuperOTC/NotoSansCJK.ttc.zip -L -o NotoSansCJK.ttc.zip \
 && curl https://github.com/googlefonts/noto-cjk/releases/download/Serif2.002/01_NotoSerifCJK.ttc.zip -L -o NotoSerifCJK.ttc.zip \
 && unzip NotoSansCJK.ttc.zip \
 && unzip NotoSerifCJK.ttc.zip \
 && mkdir /usr/local/share/fonts/ \
 && mv *.ttc /usr/local/share/fonts/ \
 && fc-cache -sf
