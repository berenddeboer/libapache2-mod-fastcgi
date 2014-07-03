How to build:

# Make sure multiverse is enabled in /etc/apt/sources.list.
# Install build tools
    sudo apt-get install devscripts
# Install package build dependencies:
    sudo apt-get build-dep libapache2-mod-fastcgi
# Build:
    dpkg-buildpackage -rfakeroot -b
