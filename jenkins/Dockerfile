FROM jenkins/jenkins:2.440

# Install Jenkins configuration-as-code plugin
RUN jenkins-plugin-cli --plugins configuration-as-code:1763.vb_fe9c1b_83f7b
# Install Jenkins influxdb plugin
RUN jenkins-plugin-cli --plugins influxdb:3.6
# Install Jenkins credentials plugin
RUN jenkins-plugin-cli --plugins credentials:1311.vcf0a_900b_37c2


## Create secrets for Jenkins configuration-as-code plugin and credentials plugin
# The documentation for the Jenkins configuration-as-code plugin says that secrets
# should be mounted as files in the /run/secrets directory.
#https://github.com/jenkinsci/configuration-as-code-plugin/blob/master/docs/features/secrets.adoc#secret-sources

# the directory /run/secrets is owned by root, so we need to change the owner to jenkins
USER root
RUN mkdir /run/secrets -p
RUN chown -R jenkins:jenkins /run/secrets
USER jenkins

# get InfluxDB credentials from build args (see docker-compose.yml)
ARG INFLUXDB_USER
ARG INFLUXDB_PASS
# generate secrets files as per documentation
RUN echo "${INFLUXDB_USER}" > /run/secrets/INFLUXDB_USER
RUN echo "${INFLUXDB_PASS}" > /run/secrets/INFLUXDB_PASS