FROM selenoid/base:7.0

ARG VERSION
ARG PACKAGE=google-chrome-stable
ARG INSTALL_DIR=chrome

LABEL browser=$PACKAGE:$VERSION

RUN \
        wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add - && \
        echo 'deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main' > /etc/apt/sources.list.d/google.list && \
        apt-get update && \
        apt-get -y --no-install-recommends install iproute2 $PACKAGE=$VERSION && \
        chown root:root /opt/google/$INSTALL_DIR/chrome-sandbox && \
        chmod 4755 /opt/google/$INSTALL_DIR/chrome-sandbox && \
        google-chrome --version && \
        rm -Rf /tmp/* && rm -Rf /var/lib/apt/lists/*
