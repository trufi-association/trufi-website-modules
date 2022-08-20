# Module `Wordpress`

## Description

The well known CMS (Content Management System) "Wordpress". Started as a simple way of creating blogging websites it is the nowadays most used CMS world wide to create websites not limited to just blogging.

## How to use

## Standard way

Modify `run.env` and run

```bash
sudo docker-compose up --env-file run.env up --build --detach
```

### FastCGI way (the alternative)

Not tested but known to make problems (also being less secure as there is no proper nginx configuration here).

TODO: Make this work and secure to use

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

5. `mv nginx.conf nginx.conf.original`

6. `mv docker-compose.yml docker-compose.yml.original`

7. `mv nginx.conf.alternative nginx.conf`

Now you are ready to serve this with a PHP enabled web server. But you want to modify the `volumes` section in file `docker-compose.yml` and probably also the nginx configuration.

#### Usage with `trufi-server-multi`

Before running `add_module`:

1. Perform the steps above
1. Modify the `fastcgi_pass` parameter in `nginx.conf` to match the name of the `php8` docker container e.g. `php8` --> `php8-php8-global`.
