# Module `php8`

## Description

Provides the fpm version of php8. PHP is a server side scripting language powering various CMS' ranging from MyPHPAdmin to Wordpress. This module is only useful in conjunction with a fastcgis capable web server.

## How to use

### With `trufi-server-multi`

Change the volume specified in `docker-compose.yml` from `./data` to `../../data/www` to match the root www folder of the `chief-nginx`. Just create one instance for e.g. a city called `global` or `helpers` where all modules providing services to other modules are into.
