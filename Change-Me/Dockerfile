FROM php:7.4-apache AS customer
RUN rm  -rf /var/www/html/
RUN mkdir /var/www/a2billing
COPY customer  /var/www/a2billing/customer
COPY common  /var/www/a2billing/common
COPY admin  /var/www/a2billing/admin
COPY agent  /var/www/a2billing/agent
RUN chown -R www-data:www-data /var/www/a2billing
RUN mkdir -p /var/lib/a2billing/script
RUN mkdir -p /var/run/a2billing
RUN rm -rf /etc/apache2/sites-available/000-default.conf
RUN rm -rf /etc/apache2/sites-enabled/000-default.conf
RUN rm -rf /etc/apache2/sites-enabled/default-ssl.conf
RUN rm -rf /etc/apache2/sites-available/default-ssl.conf
COPY customer.conf /etc/apache2/sites-available/customer.conf
RUN ln -s /etc/apache2/sites-available/customer.conf /etc/apache2/sites-enabled/customer.conf
WORKDIR /var/www/a2billing
EXPOSE 80

#RUN chmod 755 /usr/local/src/a2billing/admin/templates_c

####################

FROM voipnovatos/asterisk-13  AS asterisk
RUN mkdir -p /usr/local/src/a2billing
COPY . /usr/local/src/a2billing/
RUN ln -s /usr/local/src/a2billing/a2billing.conf /etc/a2billing.conf
RUN chmod 777 /etc/asterisk
RUN touch /etc/asterisk/additional_a2billing_iax.conf 
RUN touch /etc/asterisk/additional_a2billing_sip.conf
RUN echo \#include additional_a2billing_sip.conf >> /etc/asterisk/sip.conf
RUN echo \#include additional_a2billing_iax.conf >> /etc/asterisk/iax.conf
#RUN chown -Rf www-data /etc/asterisk/additional_a2billing_iax.conf
#RUN chown -Rf www-data /etc/asterisk/additional_a2billing_sip.conf
#RUN /usr/local/src/a2billing/addons/sounds/install_a2b_sounds.sh en es
#RUN chown -R asterisk:asterisk /usr/share/asterisk/sounds/
COPY manager.conf  /etc/asterisk/
RUN mkdir -p /usr/share/asterisk/agi-bin
#RUN chown asterisk:asterisk /usr/share/asterisk/agi-bin
RUN ln -s /usr/local/src/a2billing/AGI/a2billing.php /usr/share/asterisk/agi-bin/a2billing.php
RUN ln -s /usr/local/src/a2billing/AGI/lib /usr/share/asterisk/agi-bin/lib
#RUN chmod +x /usr/share/asterisk/agi-bin/a2billing.php
#RUN chmod +x /usr/share/asterisk/agi-bin/a2billing_monitoring.php
COPY extensions.conf /etc/asterisk/extensions.conf 
EXPOSE 5060

