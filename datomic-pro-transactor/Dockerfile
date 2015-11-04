FROM istareldritch/datomic-pro-base

MAINTAINER Ruben Paz "me@ruben.io"

COPY transactor.properties $DATOMIC_HOME/transactor.properties

CMD ./bin/transactor transactor.properties

EXPOSE 4334 4335 4336
