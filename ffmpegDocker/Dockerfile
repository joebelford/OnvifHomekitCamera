# Build stage
# Use same version as the host until I figure out avahi in Docker
FROM debian:11.5
ARG FFMPEG_SHA=100939695307743396e30e6310d2ea9cf42f9aab
ARG FFMPEG_PATCH=0001-fixed-SSRC-U_INT-issue.patch
RUN echo ========== Install dependencies ========== \
  && apt-get update && apt-get install -y \
    git \
    libssl-dev \
    libx264-dev \
    i965-va-driver \
    libva-dev \
    build-essential \
    wget \
    yasm \
    pkg-config \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/*
RUN git clone git://git.videolan.org/git/ffmpeg.git
WORKDIR /ffmpeg
RUN git checkout ${FFMPEG_SHA}
COPY /${FFMPEG_PATCH} ./
RUN git config user.email "root@localhost" \
&& git config user.name "root" \
&& git am ./${FFMPEG_PATCH}
# Add  --disable-programs for production
RUN ./configure \
  --enable-gpl \
  --enable-version3 \
  --enable-nonfree \
  --enable-libx264 \
  --enable-vaapi \
  --enable-shared \
  --enable-openssl \
  --disable-ffplay \
  --disable-ffprobe \
  --disable-doc
RUN make
RUN make install
WORKDIR /
RUN rm -rf /ffmpeg
WORKDIR /build