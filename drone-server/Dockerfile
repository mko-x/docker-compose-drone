FROM drone/drone:alpine
LABEL author="code@m.-ko.de"

# add bash for mkdir
RUN apk add --no-cache bash && \
      mkdir -p /var/lib/drone
# rm bash
RUN apk del bash

# provide lib volume
VOLUME [ "/var/lib/drone" ]

# expose explicitly
EXPOSE 8000
EXPOSE 9000
EXPOSE 80
EXPOSE 443
