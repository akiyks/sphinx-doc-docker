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

# Additional packages for latexdocs, epubdocs, and pdfdocs (no-CJK)
RUN zypper refresh \
 && zypper --non-interactive install --no-recommends \
      $pythonrev-Sphinx-latex \
      texlive-tex-gyre \
      texlive-xetex \
      texlive-pict2e \
      texlive-ellipse \
      dejavu-fonts \
      rsvg-convert \
      poppler-tools \
 && zypper clean --all

# Leap 15.6 has Inkscape 1.0.1.  It is not good enough for some of
# SVG figures drawn by Inkscape 1.4.x.
# Install Inkscape from flathub.
RUN zypper refresh \
 && zypper --non-interactive install --no-recommends \
      flatpak \
      flatpak-xdg-utils \
 && zypper clean --all \
 && flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo \
 && flatpak install -y flathub org.gnome.Platform/x86_64/48 \
 && flatpak install -y flathub org.inkscape.Inkscape

COPY inkscape-sh /usr/local/bin/inkscape
RUN chmod +x /usr/local/bin/inkscape
COPY 09-texlive-fonts.conf /etc/fonts/conf.d/
RUN fc-cache -sf
