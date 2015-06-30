FROM maestrodev/build-agent
MAINTAINER Joshua Boyd "boyd_joshua@bah.com"

USER root

RUN yum install -y ca-certificates
RUN update-ca-trust enable

COPY ashbmcwg.crt /etc/pki/ca-trust/source/anchors/
RUN update-ca-trust extract
