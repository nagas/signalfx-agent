ARG POSTGRES_VERSION=11-alpine
FROM postgres:${POSTGRES_VERSION}

CMD ["postgres", "-c", "shared_preload_libraries=pg_stat_statements"]

RUN apk add --no-cache unzip wget bash
WORKDIR /opt
RUN wget --no-check-certificate https://sp.postgresqltutorial.com/wp-content/uploads/2019/05/dvdrental.zip &&\
    unzip dvdrental.zip &&\
	tar -xf dvdrental.tar &&\
	sed -i -e 's/\$\$PATH\$\$/\/opt/' ./restore.sql &&\
	chmod 777 /opt/*

COPY init.sh /docker-entrypoint-initdb.d/
