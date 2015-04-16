FROM dockerfile/java:oracle-java8
MAINTAINER nicolasm <nicolas.c.morel@capgemini.com>

# Install NodeJS & npm
ENV NODE_VERSION 0.10.38
ENV NPM_VERSION 2.7.5

RUN curl -SLO "http://nodejs.org/dist/v$NODE_VERSION/node-v$NODE_VERSION-linux-x64.tar.gz" \
	&& tar -xzf "node-v$NODE_VERSION-linux-x64.tar.gz" -C /usr/local --strip-components=1 \
	&& rm "node-v$NODE_VERSION-linux-x64.tar.gz" \
	&& npm install -g npm@"$NPM_VERSION" \
	&& npm cache clear

# Install Bower & Gulp
RUN npm install -g bower gulp

# Install maven
RUN \
  apt-get update && \
  apt-get -y install maven && \
  rm -rf /var/lib/apt/lists/*

# Add a user
RUN adduser --disabled-password --home=/home/user --gecos "" user

# Run all operations in user mode
USER user
ENV HOME /home/user
WORKDIR /home/user
