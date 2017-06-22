FROM jetbrains/teamcity-minimal-agent:latest

# Install Python stuff
RUN apt-get update && apt-get install -y \
    build-essential \
    checkinstall \
    libreadline-gplv2-dev \
    libncursesw5-dev \
    libssl-dev \
    libsqlite3-dev \
    tk-dev \
    libgdbm-dev \
    libc6-dev \
    libbz2-dev \
    wget \
    locales

# Set the locale
RUN locale-gen en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8

RUN cd /usr/src && wget https://www.python.org/ftp/python/3.6.1/Python-3.6.1.tgz && tar xzf Python-3.6.1.tgz

RUN cd /usr/src/Python-3.6.1 && ./configure && make altinstall

RUN apt-get update && apt-get install -y \
    git \
    # python stuff
    python3-pip \
    software-properties-common \
    # pg
    libpq-dev \
    # images
    libjpeg-dev \
    zlib1g-dev \
    libpng12-dev

# nodejs 
# nvm environment variables
ENV NVM_DIR /usr/local/nvm
ENV NODE_VERSION 6.9.2

# install nvm
# https://github.com/creationix/nvm#install-script
RUN curl --silent -o- https://raw.githubusercontent.com/creationix/nvm/v0.31.2/install.sh | bash

# install node and npm
RUN source $NVM_DIR/nvm.sh \
    && nvm install $NODE_VERSION \
    && nvm alias default $NODE_VERSION \
    && nvm use default

# add node and npm to path so the commands are available
ENV NODE_PATH $NVM_DIR/v$NODE_VERSION/lib/node_modules
ENV PATH $NVM_DIR/versions/node/v$NODE_VERSION/bin:$PATH

# confirm installation
RUN node -v
RUN npm -v