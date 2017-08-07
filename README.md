# Supercronic evaluation

[supercronic](https://github.com/aptible/supercronic) is a cron-like utility
for use within containers.

This example project implements a scheduled task using supercronic.

Details and example usage are in [Dockerfile](Dockerfile) and
[docker-compose.yml](docker-compose.yml).

# Evaluation notes

Supercronic's [releases page](https://github.com/aptible/supercronic/releases)
includes stanzas for including in a Dockerfile. This made it fairly easy to
spin up.

# Sample usage

```
docker run --rm -it bennettp123/supercronic-example


```

# Customizing

```
docker run --rm -it -v ./another-sample-crontab:/etc/crontab:ro bennettp123/supercronic-example

```

