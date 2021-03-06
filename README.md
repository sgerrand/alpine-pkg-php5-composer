# alpine-pkg-php5-composer

[![CircleCI](https://img.shields.io/circleci/project/sgerrand/alpine-pkg-php5-composer/master.svg)](https://circleci.com/gh/sgerrand/alpine-pkg-php5-composer)

This is [Composer][composer] as an Alpine Linux package.

## Releases

See the [releases page](https://github.com/sgerrand/alpine-pkg-php5-composer/releases) for the latest
download links.

## Installing

The current installation method for these packages is to pull them in using
`wget` or `curl` and install the local file with `apk`:

    apk --no-cache add ca-certificates wget
    wget --quiet --output-document=/etc/apk/keys/sgerrand.rsa.pub https://alpine-pkgs.sgerrand.com/sgerrand.rsa.pub
    wget https://github.com/sgerrand/alpine-pkg-php5-composer/releases/download/1.6.2-r0/php5-composer-1.6.2-r0.apk
    apk add --no-cache php5-composer-1.6.2-r0.apk

[composer]: https://getcomposer.org
