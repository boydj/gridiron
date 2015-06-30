FROM jenkins 
MAINTAINER Joshua Boyd "boyd_joshua@bah.com"

USER root

# Use tini to work around the PID 1 problem
# TODO: Replace with my_init
ADD tini /tini
RUN chmod +x /tini

RUN apt-get update && apt-get install parallel -y

COPY ashbmcwg.crt /usr/local/share/ca-certificates/
RUN update-ca-certificates

COPY plugins.sh /usr/local/bin/plugins.sh
RUN chmod +x /usr/local/bin/plugins.sh

ENTRYPOINT ["/tini", "--", "/usr/local/bin/jenkins.sh"]

USER jenkins

COPY plugins.txt /plugins.txt
RUN /usr/local/bin/plugins.sh /plugins.txt
