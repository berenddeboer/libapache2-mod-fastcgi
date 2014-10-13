What is does
============
libapache2-mod-fastcgi has the annoying property to fail when AWS ELB
CNAME returns multiple ip addresses instead of simply picking the
first one.

The error message is something like:

  FastCgiExternalServer /usr/lib/cgi-bin/php5-fcgi: failed to resolve "internal-php-farm.ap-southeast-2.elb.amazonaws.com" to exactly one IP address

How to build
============

# Make sure multiverse is enabled in /etc/apt/sources.list.
# Make sure you have deb-src lines in /etc/apt/sources.list.
# Install build tools
    sudo apt-get install devscripts
# Install package build dependencies:
    sudo apt-get build-dep libapache2-mod-fastcgi
# Build:
    dpkg-buildpackage -rfakeroot -b
