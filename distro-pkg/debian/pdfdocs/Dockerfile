ARG distro=debian
ARG tag=stable-slim
FROM $distro:$tag
# for pdfdocs (non CJK)
RUN apt-get update \
 && apt-get upgrade -y \
 && apt-get install -y locales \
 && localedef -i en_US -c -f UTF-8 -A /usr/share/locale/locale.alias en_US.UTF-8 \
 && apt-get autoremove -y \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/*

ENV LANG en_US.utf8
RUN apt-get update \
 && DEBIAN_FRONTEND=noninteractive TZ=UTC apt-get install -y tzdata \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/*

RUN apt-get update \
 && apt-get install -y --no-install-recommends \
    perl \
    make \
    python3-sphinx \
    python3-yaml \
    graphviz \
    inkscape \
    fonts-liberation \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/*

WORKDIR /linux
CMD bash

# texlive packages
RUN apt-get update \
 && apt-get install --no-install-recommends -y \
      latexmk \
      lmodern \
      tex-gyre \
      fonts-dejavu \
      texlive-fonts-recommended \
      texlive-latex-extra \
      texlive-xetex \
      tex-common \
      dvipng \
      dvisvgm \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/*
