## Datomic Docker Bundle

This is an example of how to use the [datomic pro base docker image](https://hub.docker.com/r/istareldritch/datomic-pro-base/) to create any datomic related container.

The datomic-pro-base image is uses the [pointslope datomic-pro-starter](https://hub.docker.com/r/pointslope/datomic-pro-starter/) as base.

### Setup

The base image requires you to specify a `.credentials` file besides your Dockerfile configuration. This is used to download the datomic pro binaries.

You should specify both, the user and download key in this file. You can find them in your [My datomic account](https://my.datomic.com/account)


Datomic exposes several `ENV` variables:

- $DATOMIC_HOME is the location of the datomic original files
- $DATOMIC_VERSION is the datomic version to download.

You can use both in your `Dockerfile` and even override the `$DATOMIC_VERSION` to download the version of datomic that fits your needs.

`datomic-pro-base` sets the WORKDIR by default to $DATOMIC_HOME. That makes easy to access the binaries in your custom Dockerfile. The following is an example of how to setup a transactor using this image:

```
FROM istareldritch/datomic-pro-base

MAINTAINER Ruben Paz "me@ruben.io"

COPY transactor.properties $DATOMIC_HOME/transactor.properties

CMD ./bin/transactor transactor.properties

EXPOSE 4334 4335 4336
```

If you want to use this remember to modify also the `transactor.properties` to fit your needs and also set the license-key for datomic.
