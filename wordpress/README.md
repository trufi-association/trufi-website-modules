# Module `Wordpress`

## Description

The well known CMS (Content Management System) "Wordpress". Started as a simple way of creating blogging websites it is the nowadays most used CMS world wide to create websites not limited to just blogging.

## How to use

### Standard way

This module does not ship Wordpress but contains the meta structure to make it work with our structure and shows you how to download & integrate that CMS.

1. Download [Wordpress](https://wordpress.org/download/)
   ```bash
   curl -o wordpress.zip https://wordpress.org/latest.zip
   ```

   or if `curl` does not exist on your system
   ```bas
   wget -o wordpress.zip https://wordpress.org/latest.zip
   ```

2. `unzip wordpress.zip`

3. `rm wordpress.zip`

4. `mv wordpress www` so the name of the new folder complies with our convention and thus can be processed by automation scripts.

Now you are ready to serve this with a PHP enabled web server. But you want to modify the `volumes` section in file `docker-compose.yml` and probably also the nginx configuration.

#### Usage with `trufi-server-multi`

Before running `add_module`:

1. Perform the steps above
1. Modify the `fastcgi_pass` parameter in `nginx.conf` to match the name of the `php8` docker container e.g. `php8` --> `php8-php8-global`.

### The alternative

```bash
mv docker-compose.yml.alternative docker-compose.yml
mv nginx.conf nginx.conf.standard
mv nginx.conf.alternative nginx.conf
```

and then do the usual thing as with other modules. Configure your nginx and start this module.