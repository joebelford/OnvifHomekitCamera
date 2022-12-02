# Build stage
# FROM ubuntu:18.04
FROM joeshouse/ffmpeg
ARG USER=vscode
RUN echo ========== Install dependencies ========== \
  && apt-get update && apt-get install -y \
    clang \
    gdb \
    git \
    libavahi-compat-libdnssd-dev \
    libssl-dev \
    make \
    openssh-server \
    perl \
    unzip \
    wget \
    sudo \
    avahi-daemon \
    avahi-utils \
    libnss-mdns \
    libcurl4-openssl-dev \
    libtinfo5 \
    libturbojpeg0-dev \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/*
# RUN sed -i.bak -e 's/^#\(enable-dbus=\).*$/\1no/' /etc/avahi/avahi-daemon.conf \
# && sed -i.bak -e 's/^\(.*\$DAEMON -D\)/\1 --no-rlimits/' /etc/init.d/avahi-daemon
RUN useradd -m -s /bin/bash -G 107 $USER \
    && echo $USER ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USER \
    && chmod 0440 /etc/sudoers.d/$USER
USER vscode
WORKDIR /build
