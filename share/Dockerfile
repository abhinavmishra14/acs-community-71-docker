ARG SHARE_TAG
FROM alfresco/alfresco-share:${SHARE_TAG}

ARG TOMCAT_DIR=/usr/local/tomcat

# Server data
ARG SERVER_NAME


RUN sed -i '/Connector port="8080"/a scheme="https" secure="true"' /usr/local/tomcat/conf/server.xml && \
    sed -i "/Connector port=\"8080\"/a proxyName=\"${SERVER_NAME}\" proxyPort=\"80\"" /usr/local/tomcat/conf/server.xml




# Install modules and addons
RUN mkdir -p $TOMCAT_DIR/amps
COPY modules/amps $TOMCAT_DIR/amps
COPY modules/jars $TOMCAT_DIR/webapps/share/WEB-INF/lib

COPY cors-filter-2.5.jar $TOMCAT_DIR/webapps/share/WEB-INF/lib/
COPY java-property-utils-1.9.1.jar $TOMCAT_DIR/webapps/share/WEB-INF/lib/

COPY web.xml $TOMCAT_DIR/webapps/share/WEB-INF/

RUN java -jar $TOMCAT_DIR/alfresco-mmt/alfresco-mmt*.jar install \
    $TOMCAT_DIR/amps $TOMCAT_DIR/webapps/share -directory -nobackup -force

# Fix for https://github.com/Alfresco/acs-community-packaging/issues/367 in Share 6.2.0
COPY web-extension/share-config-custom-dev.xml $TOMCAT_DIR/shared/classes/alfresco/web-extension/
