FROM openjdk:8-jre-stretch

ENV OPENFIRE_VERSION=4.4.0 \
    OPENFIRE_USER=openfire \
    OPENFIRE_DATA_DIR=/var/lib/openfire \
    OPENFIRE_LOG_DIR=/var/log/openfire

# RUN apt-get update \
#  && apt-get install -y --no-install-recommends default-jre-headless 
# RUN apt-get update && \
#     DEBIAN_FRONTEND=noninteractive \
#     apt-get -y install default-jre-headless && \
#     apt-get clean && \
#     rm -rf /var/lib/apt/lists/*

RUN apt-get update \
 && DEBIAN_FRONTEND=noninteractive apt-get install -y openjdk-8-jre sudo wget \
 && echo "Downloading openfire_${OPENFIRE_VERSION}_all.deb ..." \
 && wget --no-verbose "http://download.igniterealtime.org/openfire/openfire_${OPENFIRE_VERSION}_all.deb" -O /tmp/openfire_${OPENFIRE_VERSION}_all.deb

RUN dpkg -i /tmp/openfire_${OPENFIRE_VERSION}_all.deb \
 && mv /var/lib/openfire/plugins/admin /usr/share/openfire/plugin-admin \
 && rm -rf openfire_${OPENFIRE_VERSION}_all.deb \
 && rm -rf /var/lib/apt/lists/*

COPY mysql-connector-java-8.0.12.jar /usr/share/openfire/lib/mysql.jar
COPY openfire_mysql.sql /usr/share/openfire/resources/database/openfire_mysql.sql

# COPY entrypoint.sh /sbin/entrypoint.sh
# RUN chmod 755 /sbin/entrypoint.sh

EXPOSE 3478/tcp 3479/tcp 5222/tcp 5223/tcp 5229/tcp 5275/tcp 5276/tcp 5262/tcp 5263/tcp 7070/tcp 7443/tcp 7777/tcp 9090/tcp 9091/tcp
VOLUME ["${OPENFIRE_DATA_DIR}"]
# ENTRYPOINT ["/sbin/entrypoint.sh"]