ARG rel=latest
FROM alpine:$rel
ENV LANG=C.UTF-8 LC_ALL=C.UTF-8 TEXLIVE_INSTALL_NO_CONTEXT_CACHE=1 NOPERLDOC=1
RUN apk -U add --no-cache \
      make \
      perl \
      python3 \
      py3-sphinx \
      py3-yaml \
      graphviz \
      rsvg-convert \
      bash \
      grep \
      sed \
      coreutils \
      font-liberation \
      font-dejavu
WORKDIR /linux
CMD /bin/bash

# for pdfdocs (w/o CJK)
RUN apk -U add --no-cache \
      texlive-xetex \
      texmf-dist-latexextra

# for pdfdocs (w CJK)  --- Doesn't work at the moment (xdvipdfmx crash)
#RUN apk -U add --no-cache \
#      font-noto-cjk \
#      texmf-dist-langchinese
