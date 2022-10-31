FROM mysql:5.7
COPY a2billing-schema-v1.4.0.sql /docker-entrypoint-initdb.d/
#RUN rm -rf /docker-entrypoint-initdb.d/UPDATE-a2billing-v1.2.0-to-v1.2.2.sql
#RUN rm -rf /docker-entrypoint-initdb.d/UPDATE-a2billing-v1.2.2-to-v1.2.3.sql
#RUN rm -rf /docker-entrypoint-initdb.d/UPDATE-a2billing-v1.2.3-to-v1.3.0.sql
#RUN rm -rf /docker-entrypoint-initdb.d/UPDATE-a2billing-v1.3.0-to-v1.3.1.sql
#RUN rm -rf /docker-entrypoint-initdb.d/UPDATE-a2billing-v1.3.3-to-v1.3.4.sql
#RUN rm -rf /docker-entrypoint-initdb.d/UPDATE-a2billing-v1.3.4-to-v1.4.0.sql
#RUN rm -rf  /docker-entrypoint-initdb.d/install-db.sh
ENV MYSQL_DATABASE mya2billing
ENV MYSQL_PASSWORD a2billing
ENV MYSQL_USER a2billinguser

