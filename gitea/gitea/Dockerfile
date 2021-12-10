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
    gmp \
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
    curl \
    libxslt-dev \
    libxml2-dev \
    py3-pillow \
    py3-pyzmq

ENV TESTING_DEPS \
#    pandoc \
    py3-pillow \
    libxml2-dev \
    libxslt-dev

ENV PYTHON_LIBS \
    jupyter \
    notebook \
    pptx2md
#    matplotlib \
#    docutils \
#    nbconvert
    
# Install/Build Packages
RUN echo "nameserver 8.8.8.8" > /etc/resolv.conf; \
#    apk add --virtual .build-deps $BUILD_DEPS && \
    apk add --virtual .persistent-deps $PERSISTENT_DEPS && \
    apk add $TESTING_DEPS --repository=http://dl-cdn.alpinelinux.org/alpine/edge/testing/ && \
    rm -rf /var/cache/apk/*
    
RUN echo "nameserver 8.8.8.8" > /etc/resolv.conf; \
	pip3 install --upgrade pip;\
	pip3 install $PYTHON_LIBS

# as of Dec 10 2021 pandoc install is broken via apk so we do it manually 	
RUN wget -c https://github.com/jgm/pandoc/releases/download/2.16.2/pandoc-2.16.2-linux-amd64.tar.gz -O - | tar -xz; \
        ln -s "$(pwd)"/pandoc-2.16.2/bin/pandoc /usr/bin/pandoc;

# add above any other python package you may need to install
