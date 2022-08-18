FROM gitpod/workspace-full

USER gitpod

RUN brew install httpie && \
    brew install bat && \
    brew install exa

EXPOSE 8091 8092 8093 8094 8095 8096 11207 11210 11211 18091 18092 18093 18094 18095 18096

RUN curl -O https://packages.couchbase.com/releases/couchbase-release/couchbase-release-1.0-amd64.deb && \
    sudo dpkg -i ./couchbase-release-1.0-amd64.deb && \
    sudo apt-get update && \
    sudo apt-get install couchbase-server-community -y && \
    rm ./couchbase-release-1.0-amd64.deb  && \
    rm core.*

