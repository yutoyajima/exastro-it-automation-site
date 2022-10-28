FROM python:3.9.9

ARG HTTP_PROXY=${HTTP_PROXY}
ENV HTTP_PROXY=${HTTP_PROXY} \
    HTTPS_PROXY=${HTTP_PROXY} \
    http_proxy=${HTTP_PROXY} \
    https_proxy=${HTTP_PROXY} \
    NO_PROXY=localhost,127.0.0.1 \
    no_proxy=localhost,127.0.0.1

RUN echo $HTTP_PROXY
RUN apt-get update
RUN apt-get install -y ca-certificates fonts-ipafont plantuml \
 && update-ca-certificates

# RUN mkdir -p /root/.pip/ && \
#     echo -e "[global]\nproxy = ${HTTP_PROXY}" > /root/.pip/pip.conf

RUN set -eux && \
    python -m pip install --proxy=$HTTP_PROXY --upgrade pip && \
    python -m pip install --proxy=$HTTP_PROXY sphinx sphinx-autobuild rstcheck sphinxcontrib-blockdiag sphinxcontrib-blockdiag sphinxcontrib-seqdiag sphinxcontrib-actdiag sphinxcontrib-nwdiag sphinx-copybutton

RUN set -eux && \
    mkdir -p /workspace

RUN wget https://github.com/jgm/pandoc/releases/download/2.19.2/pandoc-2.19.2-1-amd64.deb -O /tmp/pandoc.deb && \
    dpkg -i /tmp/pandoc.deb

WORKDIR /workspace