ARG distro=debian
ARG tag=stable-slim
FROM $distro:$tag
ENV LANG C.UTF-8

# for htmldocs
RUN apt-get update \
 && apt-get upgrade -y \
 && DEBIAN_FRONTEND=noninteractive TZ=UTC apt-get install -y tzdata \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/*

RUN apt-get update \
 && apt-get install -y --no-install-recommends \
    perl \
    make \
    python3-sphinx \
    python3-yaml \
    python3-sphinx-rtd-theme \
    graphviz \
    inkscape \
    fonts-liberation \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/*

WORKDIR /linux
CMD bash
