FROM docker.elastic.co/logstash/logstash:8.13.4

# Copy your pipeline configuration (including subfolders)
COPY pipeline/ /usr/share/logstash/pipeline/

# Copy your Logstash configuration
COPY config/logstash.yml /usr/share/logstash/config/logstash.yml

# Define persistent data storage
VOLUME ["/usr/share/logstash/data"]

# Adjust permissions
USER root
RUN chown -R logstash:logstash /usr/share/logstash/data
USER logstash
