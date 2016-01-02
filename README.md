# What is does

libapache2-mod-fastcgi has the annoying property to fail when AWS ELB
CNAME returns multiple ip addresses instead of simply picking the
first one.

The error message is something like:

  FastCgiExternalServer /usr/lib/cgi-bin/php5-fcgi: failed to resolve "internal-php-farm.ap-southeast-2.elb.amazonaws.com" to exactly one IP address

This improved version picks the first available ip address and sets a TTL
of 60 seconds. Every 60 seconds the DNS is queried for a new ip address.


# How to build

1. Make sure multiverse is enabled in /etc/apt/sources.list.
2. Make sure you have deb-src lines in /etc/apt/sources.list.
3. Install build tools
    sudo apt-get install devscripts
4. Install package build dependencies:
    sudo apt-get build-dep libapache2-mod-fastcgi
5. Make sure gcc 4.9 is installed and the default.
6. Build:
    dpkg-buildpackage -rfakeroot -b
