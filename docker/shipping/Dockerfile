FROM weaveworksdemos/msd-java:jre-latest

WORKDIR /usr/src/app
COPY *.jar ./app.jar
COPY newrelic /newrelic

RUN	chown -R ${SERVICE_USER}:${SERVICE_GROUP} ./app.jar
RUN	chown -R ${SERVICE_USER}:${SERVICE_GROUP} /newrelic

USER ${SERVICE_USER}

ARG BUILD_DATE
ARG BUILD_VERSION
ARG COMMIT

LABEL org.label-schema.vendor="Weaveworks" \
  org.label-schema.build-date="${BUILD_DATE}" \
  org.label-schema.version="${BUILD_VERSION}" \
  org.label-schema.name="Socks Shop: Shipping" \
  org.label-schema.description="REST API for Shipping service" \
  org.label-schema.url="https://github.com/Azumaxoid/shipping" \
  org.label-schema.vcs-url="github.com:Azumaxoid/shipping.git" \
  org.label-schema.vcs-ref="${COMMIT}" \
  org.label-schema.schema-version="1.0"

ENTRYPOINT ["/usr/local/bin/java.sh","-javaagent:/newrelic/newrelic.jar", "-jar","./app.jar", "--port=80"]
