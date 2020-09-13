FROM gitea/gitea:latest

# pandoc install from https://hub.docker.com/r/portown/alpine-pandoc/dockerfile
# and from here: https://github.com/skyzyx/alpine-pandoc/blob/master/Dockerfile

#RUN echo "nameserver 8.8.8.8" > /etc/resolv.conf;\
#	 apk --no-cache add --update gcc g++ python3-dev py3-pip libffi-dev asciidoctor pandoc && rm -rf /var/cache/apk/*
# install any other package you need for your external renderers

ENV BUILD_DEPS \
    alpine-sdk \
    cabal \
    coreutils \
    ghc \
    libffi \
    musl-dev \
    zlib-dev
ENV PERSISTENT_DEPS \
    gcc \
    g++ \
    python3-dev \
    py3-pip \
    libffi-dev \
    asciidoctor \
    gmp \
    curl \
    pandoc

ENV PANDOC_VERSION 2.10.1
ENV PANDOC_DOWNLOAD_URL https://github.com/jgm/pandoc/archive/$PANDOC_VERSION.tar.gz
ENV PANDOC_ROOT /usr/local/pandoc

ENV PATH $PATH:$PANDOC_ROOT/bin

# Install/Build Packages
RUN echo "nameserver 8.8.8.8" > /etc/resolv.conf; \
    apk add --no-cache -X http://dl-cdn.alpinelinux.org/alpine/edge/testing \
    apk upgrade --update && \
    apk add --virtual .build-deps $BUILD_DEPS && \
    apk add --virtual .persistent-deps $PERSISTENT_DEPS
#    mkdir -p /pandoc-build \
#             /var/docs && \
#    cd /pandoc-build && \
#    curl -fsSL "$PANDOC_DOWNLOAD_URL" | tar -xzf - && \
#    cd pandoc-$PANDOC_VERSION && \
#    cabal update && \
#    cabal install --only-dependencies && \
#    cabal configure --prefix=$PANDOC_ROOT && \
#    cabal build && \
#    cabal copy && \
#    cd / && \
#    rm -Rf /pandoc-build \
#           $PANDOC_ROOT/lib \
#           /root/.cabal \
#           /root/.ghc && \
#    && apk del --purge .build-deps
    
RUN echo "nameserver 8.8.8.8" > /etc/resolv.conf; \
	pip3 install --upgrade pip;\
	pip3 install jupyter notebook matplotlib docutils nbconvert
# add above any other python package you may need to install
