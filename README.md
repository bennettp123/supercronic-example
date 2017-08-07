# Supercronic evaluation

[supercronic](https://github.com/aptible/supercronic) is a cron-like utility
for use within containers.

This example project implements a scheduled task using supercronic.

Details and example usage are in [Dockerfile](Dockerfile)
and [Dockerfile-alpine](Dockerfile-alpine).

# Evaluation notes

Supercronic's [releases page](https://github.com/aptible/supercronic/releases)
includes stanzas for including in a Dockerfile. This made it fairly easy to
spin up.

# Sample usage

```
docker run --rm -it bennettp123/supercronic-example
Unable to find image 'bennettp123/supercronic-example:alpine' locally
alpine: Pulling from bennettp123/supercronic-example
88286f41530e: Already exists 
217659d07dd6: Pull complete 
206f4e25d3ad: Pull complete 
Digest: sha256:896867e72d6663b2ffdfab65276137321a7a4d79eb40d5d7c9d6aa78407d682e
Status: Downloaded newer image for bennettp123/supercronic-example:alpine
INFO[2017-08-07T02:52:47Z] read crontab: /etc/crontab                   
INFO[2017-08-07T02:53:00Z] starting                                      iteration=0 job.command="/bin/true" job.position=0 job.schedule="*    *            *     *           *"
INFO[2017-08-07T02:53:00Z] job succeeded                                 iteration=0 job.command="/bin/true" job.position=0 job.schedule="*    *            *     *           *"
^C
INFO[2017-08-07T02:53:06Z] received interrupt, shutting down            
INFO[2017-08-07T02:53:06Z] waiting for jobs to finish                   
INFO[2017-08-07T02:53:06Z] exiting                                      

```

# Customizing

You can specify a custom crontab file by overwriting /etc/crontab:

```
docker run --rm -it -v ./another-sample-crontab:/etc/crontab:ro bennettp123/supercronic-example
```

Alternatively, call supercronic with your desired cron file:

```
docker run --rm -it -v ./another-sample-crontab:/tmp/my-crontab:ro bennettp123/supercronic-example supercronic /tmp/my-crontab
```
