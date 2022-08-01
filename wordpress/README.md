# Module `Wordpress`

## Description

The well known CMS (Content Management System) "Wordpress". Started as a simple way of creating blogging websites it is the nowadays most used CMS world wide to create websites not limited to just blogging.

## How to use

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

Now you are ready to serve this with a PHP enabled web server.