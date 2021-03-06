# Prometheus Migration Tool

A tool for upgrading Prometheus setups to a newer version.

Currently, it migrates ASCII protcol buffer configurations from pre-v0.14 setups to the
respective YAML equivalent.

Install:
```
$ go get github.com/tools/godep
$ cd $GOPATH/src/github.com/prometheus/migrate
$ godep go install
```

Binary releases are also provided for [download](https://github.com/prometheus/migrate/releases).

Usage:
```
migrate -out=new_conf.yml old_conf.conf
```

Migration will not preserve comments. It is generally recommended for
larger files that are tedious to translate by hand.

Reading the configuration documentation will provide you with further insight
about new possibilities.

## Using Docker

You can also do the migration using the [prom/migrate](https://registry.hub.docker.com/u/prom/migrate/) Docker image.

For example:

```bash
docker pull prom/migrate

docker run --rm -ti -v $PWD/prom_migrate:/prom_migrate \
        prom/migrate -out=/prom_migrate/new_conf.yml /prom_migrate/old_conf.conf
```
