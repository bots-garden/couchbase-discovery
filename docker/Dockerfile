FROM gitpod/workspace-full



USER gitpod

RUN brew install httpie && \
    brew install bat && \
    brew install exa

RUN curl -O https://packages.couchbase.com/releases/couchbase-release/couchbase-release-1.0-amd64.deb && \
    sudo dpkg -i ./couchbase-release-1.0-amd64.deb && \
    sudo apt-get update && \
    sudo apt-get install couchbase-server-community -y
    