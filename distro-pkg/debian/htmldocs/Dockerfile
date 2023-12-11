ARG distro=debian
ARG tag=stable-slim
FROM $distro:$tag
# for htmldocs
RUN apt-get update \
 && apt-get upgrade -y \
 && apt-get install -y locales \
 && localedef -i en_US -c -f UTF-8 -A /usr/share/locale/locale.alias en_US.UTF-8 \
 && apt-get autoremove \
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
