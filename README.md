# Apache HTTP Server Docker Container Image

[![Build Status](https://travis-ci.org/anaxexp/apache.svg?branch=master)](https://travis-ci.org/anaxexp/apache)
[![Docker Pulls](https://img.shields.io/docker/pulls/anaxexp/apache.svg)](https://hub.docker.com/r/anaxexp/apache)
[![Docker Stars](https://img.shields.io/docker/stars/anaxexp/apache.svg)](https://hub.docker.com/r/anaxexp/apache)
[![Docker Layers](https://images.microbadger.com/badges/image/anaxexp/apache.svg)](https://microbadger.com/images/anaxexp/apache)

* [Docker images](#docker-images)
* [Environment variables](#environment-variables)
* [Enabled modules](#enabled-modules)
* [Virtual host presets](#virtual-hosts-presets)
    * [HTML](#html)
    * [PHP (FastCGI)](#php-fastcgi)
* [Customization](#customization)
* [Orchestration actions](#orchestration-actions)

## Docker Images

❗️For better reliability we release images with stability tags (`anaxexp/apache:2.4-X.X.X`) which correspond to [git tags](https://github.com/anaxexp/apache/releases). We strongly recommend using images only with stability tags. 

Overview:

* All images are based on Alpine Linux
* Base image: [anaxexp/httpd](https://github.com/anaxexp/httpd)
* [Travis CI builds](https://travis-ci.org/anaxexp/apache) 
* [Docker Hub](https://hub.docker.com/r/anaxexp/apache) 

Supported tags and respective `Dockerfile` links:

* `2.4`, `2`, `latest` [_(Dockerfile)_](https://github.com/anaxexp/apache/tree/master/Dockerfile)

## Environment Variables 

| Variable                             | Default Value                                    | Description |
| ------------------------------------ | ------------------------------------------------ | ----------- |
| `APACHE_DIRECTORY_INDEX`             | `index.html`                                     |             |
| `APACHE_GROUP`                       | `apache`                                         |             |
| `APACHE_HOSTNAME_LOOKUPS`            | `Off`                                            |             |
| `APACHE_HTTP2`                       |                                                  |             |
| `APACHE_INCLUDE_CONF`                | `conf/conf.d/*.conf`                             |             |
| `APACHE_KEEP_ALIVE_TIMEOUT`          | `5`                                              |             |
| `APACHE_KEEP_ALIVE`                  | `On`                                             |             |
| `APACHE_LIMITED_ACCESS`              |                                                  |             |
| `APACHE_LOG_LEVEL`                   | `warn`                                           |             |
| `APACHE_MAX_KEEP_ALIVE_REQUESTS`     | `100`                                            |             |
| `APACHE_MPM_EVENT_MAX_CLIENTS`       | `400`                                            |             |
| `APACHE_MPM_EVENT_SERVER_LIMIT`      | `16`                                             |             |
| `APACHE_MPM_EVENT_START_SERVERS`     | `3`                                              |             |
| `APACHE_MPM_EVENT_THREAD_LIMIT`      | `64`                                             |             |
| `APACHE_MPM_EVENT_THREADS_PER_CHILD` | `25`                                             |             |
| `APACHE_MPM`                         | `event`                                          |             |
| `APACHE_REQUEST_READ_TIMEOUT`        | `header=20-40,MinRate=500` `body=20,MinRate=500` |             |
| `APACHE_SERVER_NAME`                 | `default`                                        |             |
| `APACHE_SERVER_NAME`                 | `default`                                        |             |
| `APACHE_SERVER_SIGNATURE`            | `Off`                                            |             |
| `APACHE_SERVER_TOKENS`               | `Full`                                           |             |
| `APACHE_TIMEOUT`                     | `60`                                             |             |
| `APACHE_USE_CANONICAL_NAME`          | `Off`                                            |             |
| `APACHE_USER`                        | `apache`                                         |             |
| `APACHE_VHOST_PRESET`                | `html`                                           |             |

## Enabled Modules

The list of installed modules: https://github.com/anaxexp/apache/blob/master/tests/basic/apache_modules

## Virtual hosts presets

By default will be used `html` virtual host preset, you can change it via env var `$APACHE_VHOST_PRESET`. The list of available presets:   

### HTML

This is the default preset.

* [Preset template](https://github.com/anaxexp/apache/blob/master/templates/presets/html.conf.tmpl)
* Usage: this preset selected by default

### PHP (FastCGI)

Additional environment variables for PHP preset:

| Variable                         | Default Value   | Description |
| -------------------------------- | --------------- | ----------- |
| `APACHE_BACKEND_HOST`            | `php`           |             |
| `APACHE_BACKEND_PORT`            | `9000`          |             |
| `APACHE_DIRECTORY_INDEX`         | `index.php`     |             |
| `APACHE_FCGI_PROXY_CONN_TIMEOUT` | `5`             |             |
| `APACHE_FCGI_PROXY_TIMEOUT`      | `60`            |             |

* [Preset template](https://github.com/anaxexp/apache/blob/master/templates/presets/php.conf.tmpl)
* Usage: add `APACHE_VHOST_PRESET=php`, optionally modify `APACHE_BACKEND_HOST`

## Customization

If you can't customize a config via environment variables, you can completely override include of the virtual host config by overriding `APACHE_INCLUDE_CONF`, it will be included in `httpd.conf`.

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