FROM yandex/clickhouse-server

ARG deb_location="https://github.com/ClickHouse/ClickHouse/releases/download/"
ARG version=22.3.14.23

RUN wget --no-check-certificate ${deb_location}v${version}-lts/clickhouse-common-static_${version}_amd64.deb \
    && wget --no-check-certificate ${deb_location}v${version}-lts/clickhouse-client_${version}_amd64.deb \
    && wget --no-check-certificate ${deb_location}v${version}-lts/clickhouse-server_${version}_amd64.deb \
    && DEBIAN_FRONTEND=noninteractive dpkg -i *.deb \
    && rm -rf \
        *.deb \
        /var/lib/apt/lists/* \
        /var/cache/debconf \
        /tmp/* \
    && apt-get clean

# debug tools + symbols (optional)
#RUN apt-get update \
#    && DEBIAN_FRONTEND=noninteractive apt-get install --yes --no-install-recommends gdb binutils  linux-tools-common linux-tools-generic linux-tools-`uname -r` \
#    && wget --no-check-certificate ${deb_location}v${version}-lts/clickhouse-common-static-dbg_${version}_amd64.deb \
#    && DEBIAN_FRONTEND=noninteractive dpkg -i *.deb \
#    && rm -rf \
#        *.deb \
#        /var/lib/apt/lists/* \
#        /var/cache/debconf \
#        /tmp/* \
#    && apt-get clean