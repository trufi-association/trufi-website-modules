FROM wordpress:latest

# Deactivate apache2 logging in this image as we have a privacy friendly logging in nginx already and there is no need for reluctancy
RUN ["rm", "/var/log/apache2/access.log", "/var/log/apache2/error.log", "/var/log/apache2/other_vhosts_access.log"]
RUN ["ln", "-s", "/dev/null", "/var/log/apache2/access.log"]
RUN ["ln", "-s", "/dev/null", "/var/log/apache2/error.log"]
RUN ["ln", "-s", "/dev/null", "/var/log/apache2/other_vhosts_access.log"]
