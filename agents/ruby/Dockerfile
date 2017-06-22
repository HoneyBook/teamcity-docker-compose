FROM jetbrains/teamcity-minimal-agent:latest

# Install Python stuff
RUN apt-get update && apt-get install -y \
    build-essential checkinstall libreadline-gplv2-dev libncursesw5-dev libssl-dev libsqlite3-dev tk-dev libgdbm-dev libc6-dev libbz2-dev wget locales \
    curl patch gawk g++ gcc make libc6-dev patch zlib1g-dev libssl-dev libyaml-dev libsqlite3-dev sqlite3 autoconf libgdbm-dev libncurses5-dev automake libtool bison pkg-config libffi-dev

RUN locale-gen en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8

RUN gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3
RUN curl -sSL https://get.rvm.io | bash -s stable
#RUN source ~/.rvm/scripts/rvm
RUN /bin/bash -l -c "rvm autolibs disable"
RUN /bin/bash -l -c "rvm install 2.3.1"
RUN /bin/bash -l -c "rvm use 2.3.1 --default"
RUN /bin/bash -l -c "ruby -v"

#RUN /bin/bash -l -c "echo 'gem: --no-ri --no-rdoc' > ~/.gemrc"
RUN /bin/bash -l -c "gem install rake --no-ri --no-rdoc"
RUN /bin/bash -l -c "gem install bundler --no-ri --no-rdoc"

# Import MongoDB public GPG key AND create a MongoDB list file

