ARG rel=stable
FROM debian:$rel-slim
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
    python3-venv \
    graphviz \
    inkscape \
    fonts-liberation \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/*

COPY requirements.txt /opt/
RUN /usr/bin/python3 -m venv sphinx_2.4.5 \
 && . sphinx_2.4.5/bin/activate \
 && pip install -r /opt/requirements.txt \
 && deactivate

COPY requirements-3.1.2.txt /opt/
RUN /usr/bin/python3 -m venv sphinx_3.1.2 \
 && . sphinx_3.1.2/bin/activate \
 && pip install -r /opt/requirements-3.1.2.txt \
 && deactivate

COPY requirements-3.2.1.txt /opt/
RUN /usr/bin/python3 -m venv sphinx_3.2.1 \
 && . sphinx_3.2.1/bin/activate \
 && pip install -r /opt/requirements-3.2.1.txt \
 && deactivate

COPY requirements-3.3.1.txt /opt/
RUN /usr/bin/python3 -m venv sphinx_3.3.1 \
 && . sphinx_3.3.1/bin/activate \
 && pip install -r /opt/requirements-3.3.1.txt \
 && deactivate

COPY requirements-3.4.3.txt /opt/
RUN /usr/bin/python3 -m venv sphinx_3.4.3 \
 && . sphinx_3.4.3/bin/activate \
 && pip install -r /opt/requirements-3.4.3.txt \
 && deactivate

COPY requirements-3.5.4.txt /opt/
RUN /usr/bin/python3 -m venv sphinx_3.5.4 \
 && . sphinx_3.5.4/bin/activate \
 && pip install -r /opt/requirements-3.5.4.txt \
 && deactivate

COPY requirements-4.0.3.txt /opt/
RUN /usr/bin/python3 -m venv sphinx_4.0.3 \
 && . sphinx_4.0.3/bin/activate \
 && pip install -r /opt/requirements-4.0.3.txt \
 && deactivate

COPY requirements-4.1.2.txt /opt/
RUN /usr/bin/python3 -m venv sphinx_4.1.2 \
 && . sphinx_4.1.2/bin/activate \
 && pip install -r /opt/requirements-4.1.2.txt \
 && deactivate

COPY requirements-4.2.0.txt /opt/
RUN /usr/bin/python3 -m venv sphinx_4.2.0 \
 && . sphinx_4.2.0/bin/activate \
 && pip install -r /opt/requirements-4.2.0.txt \
 && deactivate

COPY requirements-4.3.2.txt /opt/
RUN /usr/bin/python3 -m venv sphinx_4.3.2 \
 && . sphinx_4.3.2/bin/activate \
 && pip install -r /opt/requirements-4.3.2.txt \
 && deactivate

COPY requirements-4.4.0.txt /opt/
RUN /usr/bin/python3 -m venv sphinx_4.4.0 \
 && . sphinx_4.4.0/bin/activate \
 && pip install -r /opt/requirements-4.4.0.txt \
 && deactivate

COPY requirements-4.5.0.txt /opt/
RUN /usr/bin/python3 -m venv sphinx_4.5.0 \
 && . sphinx_4.5.0/bin/activate \
 && pip install -r /opt/requirements-4.5.0.txt \
 && deactivate

COPY requirements-5.0.2.txt /opt/
RUN /usr/bin/python3 -m venv sphinx_5.0.2 \
 && . sphinx_5.0.2/bin/activate \
 && pip install -r /opt/requirements-5.0.2.txt \
 && deactivate

COPY requirements-5.1.1.txt /opt/
RUN /usr/bin/python3 -m venv sphinx_5.1.1 \
 && . sphinx_5.1.1/bin/activate \
 && pip install -r /opt/requirements-5.1.1.txt \
 && deactivate

COPY requirements-5.2.3.txt /opt/
RUN /usr/bin/python3 -m venv sphinx_5.2.3 \
 && . sphinx_5.2.3/bin/activate \
 && pip install -r /opt/requirements-5.2.3.txt \
 && deactivate

COPY requirements-5.3.0.txt /opt/
RUN /usr/bin/python3 -m venv sphinx_5.3.0 \
 && . sphinx_5.3.0/bin/activate \
 && pip install -r /opt/requirements-5.3.0.txt \
 && deactivate

COPY requirements-6.1.3.txt /opt/
RUN /usr/bin/python3 -m venv sphinx_6.1.3 \
 && . sphinx_6.1.3/bin/activate \
 && pip install -r /opt/requirements-6.1.3.txt \
 && deactivate

COPY requirements-6.2.1.txt /opt/
RUN /usr/bin/python3 -m venv sphinx_6.2.1 \
 && . sphinx_6.2.1/bin/activate \
 && pip install -r /opt/requirements-6.2.1.txt \
 && deactivate

COPY requirements-latest.txt /opt/
WORKDIR /
RUN /usr/bin/python3 -m venv sphinx_latest \
 && . sphinx_latest/bin/activate \
 && pip install -r /opt/requirements-latest.txt \
 && deactivate

WORKDIR /linux
CMD bash
