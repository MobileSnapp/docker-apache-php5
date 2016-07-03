# Apache HTTP server container to run PHP 5.x applications

[![forthebadge](http://forthebadge.com/images/badges/built-by-developers.svg)](http://www.mobilesnapp.com)

Docker images of Ubuntu 14.04 LTS with Apache2 and PHP5/Composer. 

For PHP7 please check out Ubuntu 16.04 LTS and PHP7 container under Dockbox (MobileSnapp/docker-dockbox-apache)

## Downloading

To download the image mobilesnapp/apache-php5, execute the following command:

    docker pull mobilesnapp/apache-php5

This will find the image by name on Docker Hub and download it from Docker Hub.


## Usage

    $ docker run -d -p 80:80 mobilesnapp/apache-php5
    
With all the options:
 
    $ docker run -d -p 80:80 \
        -v /home/user/app:/var/www/site \
        -e PHP_ERROR_REPORTING='E_ALL & ~E_STRICT' \
        mobilesnapp/apache-php5

-v [local path]:/var/www/site maps the container's webroot to a local path
-p [local port]:80 maps a local port to the container's HTTP port 80
-e PHP_ERROR_REPORTING=[php error_reporting settings] sets the value of error_reporting in the php.ini files.

With SSL options

    $ docker run -d -p 80:80 -p 443:443 \
        -v /home/user/app:/var/www/site \
        -e PHP_ERROR_REPORTING='E_ALL & ~E_STRICT' \
        mobilesnapp/apache-php5

## Access apache logs

Apache is configured to log both access and error log to STDOUT. So you can simply use docker logs to get the log output:

    docker logs -f container-id
    

## Enable .htaccess files

If you app uses .htaccess files you need to pass the ALLOW_OVERRIDE environment variable

    docker run -d -p 80:80 -e ALLOW_OVERRIDE=true mobilesnapp/apache-php5


## Author

MobileSnapp (support@mobilesnapp.com)