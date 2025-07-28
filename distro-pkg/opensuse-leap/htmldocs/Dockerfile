FROM opensuse/leap:latest
ARG pythonrev=python311
ARG pythoncmd=python3.11
ARG pkgname=Sphinx
# packages for htmldocs, (latexdocs is not covered)
RUN zypper refresh \
 && zypper --non-interactive install --no-recommends \
      $pythonrev-$pkgname \
      $pythonrev-PyYAML \
      perl \
      which \
      make \
      graphviz \
 && zypper clean --all
RUN if [ "$pythoncmd" = "python3" ] ; then \
      echo "already have python3" \
 ;  else \
      cd /usr/local/bin \
 &&   ln -sf /usr/bin/$pythoncmd python3 \
 ;  fi
WORKDIR /linux
CMD bash
