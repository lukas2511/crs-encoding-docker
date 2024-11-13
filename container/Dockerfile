FROM debian:bookworm

RUN apt-get -qq update && \
    apt-get -qqy dist-upgrade && \
    apt-get -qqy install ca-certificates && \
    apt-get clean

ADD etc/ /etc/

RUN apt-get -qq update && \
    apt-get -qqy install ffmpeg libboolean-perl libconfig-inifiles-perl libdatetime-perl libfile-which-perl libipc-run3-perl libjson-perl libmath-round-perl libproc-processtable-perl libwww-curl-perl libxml-rpc-fast-perl libxml-simple-perl inetutils-ping iproute2 curl && \
    rm -rf /var/*/apt /var/*/dpkg

ADD crs-scripts/ /opt/crs-scripts/
ADD usr/ /usr/

RUN useradd voc
USER voc
CMD /opt/crs-scripts/bin/crs_run script-D-encoding.pl
