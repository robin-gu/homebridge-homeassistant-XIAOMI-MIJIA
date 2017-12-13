FROM node:alpine

# RUN apt-get update && \
#   apt-get install -yq libavahi-compat-libdnssd-dev && \
#   apt-get install -yq apt-utils apt-transport-https && \
#   apt-get install -yq curl wget && \
#   apt-get install -yq libnss-mdns avahi-discover libavahi-compat-libdnssd-dev libkrb5-dev && \
#   rm -rf /var/lib/apt/lists/*
#
# RUN npm install -g --unsafe-perm homebridge && \
#   npm install -g --unsafe-perm homebridge-homeassistant

RUN apk add --no-cache tini git python make g++ libffi-dev openssl-dev avahi-compat-libdns_sd avahi-dev openrc dbus

ENV HOMEBRIDGE_VERSION 0.4.33
ENV HOMEBRIDGE_HOMEASSISTANT_VERSION 3.0.2

RUN adduser -D homebridge && \
  mkdir /config && \
  chown -R homebridge:homebridge /config
VOLUME /config

EXPOSE 5353 51826
RUN npm install -g node-gyp
USER homebridge

RUN npm install -g homebridge@$HOMEBRIDGE_VERSION homebridge-homeassistant@$HOMEBRIDGE_HOMEASSISTANT_VERSION

ENTRYPOINT ["/sbin/tini", "--"]
CMD ["homebridge","-U","/config"]
