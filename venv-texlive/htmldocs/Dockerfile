ARG rel=stable
ARG distro=ubuntu
FROM $distro:$rel
# for htmldocs

ENV LANG=C.UTF-8 LC_ALL=C.UTF-8
RUN apt-get update \
 && DEBIAN_FRONTEND=noninteractive TZ=UTC apt-get install -y tzdata \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/*

RUN apt-get update \
 && apt-get install -y --no-install-recommends \
    perl \
    make \
    python3-venv \
    graphviz \
    inkscape \
    fonts-liberation \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/*

COPY requirements.txt /opt/
RUN /usr/bin/python3 -m venv sphinx_venv \
 && . sphinx_venv/bin/activate \
 && pip install -U pip \
 && pip install -r /opt/requirements.txt \
 && deactivate

WORKDIR /linux
CMD bash
