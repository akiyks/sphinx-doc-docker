FROM opensuse/leap:latest
ARG pythonrev=python311
ARG pythoncmd=python3.11
# packages for htmldocs, (latexdocs is not covered)
RUN zypper refresh \
 && zypper --non-interactive install --no-recommends \
      $pythonrev-Sphinx \
      $pythonrev-PyYAML \
      perl \
      which \
      make \
      graphviz \
 && zypper clean --all \
 && cd /usr/bin \
   && ln -s $pythoncmd python3

WORKDIR /linux
CMD bash
