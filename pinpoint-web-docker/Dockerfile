FROM tomcat:8-jre8

ENV PINPOINT_VERSION=1.7.1

ADD start-web.sh /usr/local/bin/

RUN chmod a+x /usr/local/bin/start-web.sh \
    && mkdir -p /assets/ \
    && curl -fSL https://raw.githubusercontent.com/naver/pinpoint/$PINPOINT_VERSION/web/src/main/resources/pinpoint-web.properties -o /assets/pinpoint-web.properties \
    && curl -fSL https://raw.githubusercontent.com/naver/pinpoint/$PINPOINT_VERSION/web/src/main/resources/hbase.properties -o /assets/hbase.properties \
    && curl -fSL https://github.com/naver/pinpoint/releases/download/$PINPOINT_VERSION/pinpoint-web-$PINPOINT_VERSION.war -o pinpoint-web.war \
    && rm -rf /usr/local/tomcat/webapps \
    && mkdir -p /usr/local/tomcat/webapps \
    && unzip pinpoint-web.war -d /usr/local/tomcat/webapps/ROOT \
    && rm -rf pinpoint-web.war

EXPOSE 8080

ENTRYPOINT ["/usr/local/bin/start-web.sh"]