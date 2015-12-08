# What is does

libapache2-mod-fastcgi has the annoying property to fail when AWS ELB
CNAME returns multiple ip addresses instead of simply picking the
first one.

The error message is something like:

  FastCgiExternalServer /usr/lib/cgi-bin/php5-fcgi: failed to resolve "internal-php-farm.ap-southeast-2.elb.amazonaws.com" to exactly one IP address

This improved version simply picks the first ip address. Unfortunately
it does not yet take TTL into account.


# How to build

1. Make sure multiverse is enabled in /etc/apt/sources.list.
2. Make sure you have deb-src lines in /etc/apt/sources.list.
3. Install build tools
    sudo apt-get install devscripts
4. Install package build dependencies:
    sudo apt-get build-dep libapache2-mod-fastcgi
5. Build:
    dpkg-buildpackage -rfakeroot -b
