FROM oscm-nginx

ENV SERVERNAME=oscm CORE_NAME=oscm-core CORE_PORT=8081 BRANDING_NAME=oscm-branding BRANDING_PORT=80 BIRT_NAME=oscm-birt BIRT_PORT=8680 APP_NAME=oscm-app APP_PORT=8881

COPY start.sh /opt/start.sh
COPY templates/*.template /opt/templates/
COPY ssl.crt /opt/ssl.crt
COPY ssl.key /opt/ssl.key

RUN mkdir /etc/proxy-ssl /import && \
    chmod +x /opt/start.sh && \
    SUSEConnect --cleanup && \
    if [ -f /etc/SUSEConnect ]; then rm -f /etc/SUSEConnect; fi && \
    if [ -d /etc/zypp/services.d ]; then rm -f /etc/zypp/services.d/*; fi && \
    if [ -d /etc/zypp/credentials.d ]; then rm -f /etc/zypp/credentials.d/*; fi

VOLUME /import

EXPOSE 80 443

CMD ["/opt/start.sh"]
