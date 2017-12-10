packaFROM python:alpine

RUN apk add --no-cache tini

ENV HOMEASSISTANT_VERSION 0.59.2
RUN pip install homeassistant==$HOMEASSISTANT_VERSION

RUN adduser -D homeassistant

USER homeassistant

ENTRYPOINT ["/sbin/tini", "--"]
CMD ["homeassistant"]
