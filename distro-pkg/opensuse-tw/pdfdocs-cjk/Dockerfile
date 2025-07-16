FROM opensuse/tumbleweed:latest
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
# Sans:
#   https://github.com/notofonts/noto-cjk/blob/main/Sans/OTC/NotoSansCJK-Bold.ttc
#   https://github.com/notofonts/noto-cjk/blob/main/Sans/OTC/NotoSansCJK-Regular.ttc
# Serif:
#   https://github.com/notofonts/noto-cjk/blob/main/Serif/OTC/NotoSerifCJK-Bold.ttc
#   https://github.com/notofonts/noto-cjk/blob/main/Serif/OTC/NotoSerifCJK-Regular.ttc
RUN cd /opt \
 && curl https://github.com/notofonts/noto-cjk/blob/main/Sans/OTC/NotoSansCJK-Bold.ttc -L -O \
 && curl https://github.com/notofonts/noto-cjk/blob/main/Sans/OTC/NotoSansCJK-Regular.ttc -L -O \
 && curl https://github.com/notofonts/noto-cjk/blob/main/Serif/OTC/NotoSerifCJK-Bold.ttc -L -O \
 && curl https://github.com/notofonts/noto-cjk/blob/main/Serif/OTC/NotoSerifCJK-Regular.ttc -L -O \
 && mkdir /usr/local/share/fonts/ \
 && mv *.ttc /usr/local/share/fonts/ \
 && fc-cache -sf
