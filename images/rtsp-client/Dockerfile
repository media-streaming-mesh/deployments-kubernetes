FROM  ubuntu:20.04

RUN     apt-get -yqq update && \
        apt-get install -yq --no-install-recommends ca-certificates expat ffmpeg && \
        apt-get autoremove -y && \
        apt-get clean -y

CMD tail -f /dev/null
