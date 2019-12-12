# Gstreamer build artifacts

FROM debian:buster

ENV GSTREAMER_VERSION="1.16.2"

RUN apt-get update && apt-get install -y --no-install-recommends \
    autoconf `# libnice` \
    automake `# libnice` \
    bison \
    build-essential \
    ca-certificates \
    flex \
    gettext \
    git \
    curl \
    gnutls-dev `# libnice` \
    gtk-doc-tools `# libnice` \
    libffi-dev \
    libglib2.0 \
    libnice-dev \
    libopus-dev \
    libpcre3-dev \
    libsrtp2-dev \
    libssl-dev `# needed for DTLS requirement`\
    libtool `# libnice` \
    libvpx-dev \
    libx264-dev \
    mount \
    perl \
    python \
    wget \
    zlib1g \
    yasm \
# http://www.linuxfromscratch.org/blfs/view/svn/multimedia/gstreamer10.html
    && mkdir /build && cd /build \
    && wget https://gstreamer.freedesktop.org/src/gstreamer/gstreamer-$GSTREAMER_VERSION.tar.xz \
    && tar xvfJ gstreamer-$GSTREAMER_VERSION.tar.xz > /dev/null \
    && cd gstreamer-$GSTREAMER_VERSION \
    && ./configure --prefix=/usr \
    && make \
    && make install \
    && cd /build \
# gst-plugins-base
    && wget https://gstreamer.freedesktop.org/src/gst-plugins-base/gst-plugins-base-$GSTREAMER_VERSION.tar.xz \
    && tar xvfJ gst-plugins-base-$GSTREAMER_VERSION.tar.xz > /dev/null \
    && cd gst-plugins-base-$GSTREAMER_VERSION \
    && ./configure --prefix=/usr \
    && make \
    && make install \
    && cd /build \
# libnice
    && git clone https://github.com/libnice/libnice.git \
    && cd libnice \
    && ./autogen.sh --prefix=/usr --with-gstreamer --enable-static --enable-static-plugins --enable-shared --without-gstreamer-0.10 --disable-gtk-doc \
    && make install \
    && cd /build \
# gst-plugins-good
    && wget https://gstreamer.freedesktop.org/src/gst-plugins-good/gst-plugins-good-$GSTREAMER_VERSION.tar.xz \
    && tar xvfJ gst-plugins-good-$GSTREAMER_VERSION.tar.xz > /dev/null \
    && cd gst-plugins-good-$GSTREAMER_VERSION \
    && ./configure --prefix=/usr \
    && make \
    && make install \
    && cd /build \
# gst-plugins-bad
    && wget https://gstreamer.freedesktop.org/src/gst-plugins-bad/gst-plugins-bad-$GSTREAMER_VERSION.tar.xz \
    && tar xvfJ gst-plugins-bad-$GSTREAMER_VERSION.tar.xz > /dev/null \
    && cd gst-plugins-bad-$GSTREAMER_VERSION \
    && ./configure --prefix=/usr \
    && make \
    && make install \
    && cd /build \
# gst-plugins-ugly
    && wget https://gstreamer.freedesktop.org/src/gst-plugins-ugly/gst-plugins-ugly-$GSTREAMER_VERSION.tar.xz \
    && tar xvfJ gst-plugins-ugly-$GSTREAMER_VERSION.tar.xz > /dev/null \
    && cd gst-plugins-ugly-$GSTREAMER_VERSION \
    && ./configure --prefix=/usr \
    && make \
    && make install \
    && cd /build \
# gst-rtsp-server
    && wget https://gstreamer.freedesktop.org/src/gst-rtsp-server/gst-rtsp-server-$GSTREAMER_VERSION.tar.xz \
    && tar xvfJ gst-rtsp-server-$GSTREAMER_VERSION.tar.xz > /dev/null \
    && cd gst-rtsp-server-$GSTREAMER_VERSION \
    && ./configure --prefix=/usr \
    && make \
    && make install \
    && cd /build \
# gst-libav
    && wget https://gstreamer.freedesktop.org/src/gst-libav/gst-libav-$GSTREAMER_VERSION.tar.xz \
    && tar xvfJ gst-libav-$GSTREAMER_VERSION.tar.xz > /dev/null \
    && cd gst-libav-$GSTREAMER_VERSION \
    && ./configure --prefix=/usr \
    && make \
    && make install

RUN rm -rf /build
