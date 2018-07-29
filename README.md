# Apache HTTP Server Docker Container Image

[![Build Status](https://travis-ci.org/anaxexp/apache.svg?branch=master)](https://travis-ci.org/anaxexp/apache)
[![Docker Pulls](https://img.shields.io/docker/pulls/anaxexperience/apache.svg)](https://hub.docker.com/r/anaxexperience/apache)
[![Docker Stars](https://img.shields.io/docker/stars/anaxexperience/apache.svg)](https://hub.docker.com/r/anaxexperience/apache)
[![Docker Layers](https://images.microbadger.com/badges/image/anaxexperienceapache.svg)](https://microbadger.com/images/anaxexperience/apache)

## Docker Images

❗️For better reliability we release images with stability tags (`anaxexperience/apache:2.4-X.X.X`) which correspond to [git tags](https://github.com/anaxexp/apache/releases). We strongly recommend using images only with stability tags. 

Overview:

* All images are based on Alpine Linux
* Base image: [anaxexperience/httpd](https://github.com/anaxexp/httpd)
* [Travis CI builds](https://travis-ci.org/anaxexp/apache) 
* [Docker Hub](https://hub.docker.com/r/anaxexperience/apache) 

Supported tags and respective `Dockerfile` links:

* `2.4`, `2`, `latest` [_(Dockerfile)_](https://github.com/anaxexp/apache/tree/master/Dockerfile)

## Environment Variables 

| Variable                             | Default Value                                    | Description |
| ------------------------------------ | ------------------------------------------------ | ----------- |
| `APACHE_ENABLE_HEALTHZ_LOGS`         |                                                  |             |
| `APACHE_GROUP`                       | `apache`                                         |             |
| `APACHE_HOSTNAME_LOOKUPS`            | `Off`                                            |             |
| `APACHE_HTTP2`                       |                                                  |             |
| `APACHE_INCLUDE_CONF`                | `conf/conf.d/*.conf`                             |             |
| `APACHE_KEEP_ALIVE`                  | `On`                                             |             |
| `APACHE_KEEP_ALIVE_TIMEOUT`          | `5`                                              |             |
| `APACHE_LOG_LEVEL`                   | `warn`                                           |             |
| `APACHE_MAX_KEEP_ALIVE_REQUESTS`     | `100`                                            |             |
| `APACHE_MPM_EVENT_SERVER_LIMIT`      | `16`                                             |             |
| `APACHE_MPM_EVENT_MAX_CLIENTS`       | `400`                                            |             |
| `APACHE_MPM_EVENT_START_SERVERS`     | `3`                                              |             |
| `APACHE_MPM_EVENT_THREADS_PER_CHILD` | `25`                                             |             |
| `APACHE_MPM_EVENT_THREAD_LIMIT`      | `64`                                             |             |
| `APACHE_REQUEST_READ_TIMEOUT`        | `header=20-40,MinRate=500` `body=20,MinRate=500` |             |
| `APACHE_SERVER_NAME`                 | `default`                                        |             |
| `APACHE_SERVER_TOKENS`               | `Full`                                           |             |
| `APACHE_SERVER_SIGNATURE`            | `Off`                                            |             |
| `APACHE_TIMEOUT`                     | `60`                                             |             |
| `APACHE_USE_CANONICAL_NAME`          | `Off`                                            |             |
| `APACHE_USER`                        | `apache`                                         |             |

## [Enabled Modules](https://github.com/anaxexp/apache/blob/master/test/apache_modules)

## Images based on `anaxexperience/apache`

* [anaxexperience/php-apache](https://github.com/anaxexp/php-apache)

## Orchestration actions

Usage:
```
make COMMAND [params ...]

commands:
    check-ready [host max_try wait_seconds]
 
default params values:
    host localhost
    max_try 1
    wait_seconds 1
    delay_seconds 0
```
