FROM ubuntu:artful

ENV DEBIAN_FRONTEND noninteractive

# Usual update / upgrade
RUN apt-get update && apt-get upgrade -y && apt-get dist-upgrade -y

# Install requirements
RUN apt-get install -y curl supervisor

# Install nodejs
RUN curl -sL https://deb.nodesource.com/setup_5.x | bash -
RUN apt-get install --fix-missing -y nodejs

# Get slack-irc
RUN npm install -g slack-irc

# Add configurations
ADD config.json slack-irc/config.json

# Add supervisor configs
ADD supervisord.conf supervisord.conf

CMD ["-n", "-c", "/supervisord.conf"]
ENTRYPOINT ["/usr/bin/supervisord"]
