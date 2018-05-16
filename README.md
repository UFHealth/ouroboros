Ouroboros
=====

A tool to make Docker-based development easier across multiple projects.

# Installation

## Setting up DNS on Mac

For Mac we can use the `.loc` top-level domain via dnsmasq and resolver.

```
brew install dnsmasq
echo 'address=/.loc/127.0.0.1' > /usr/local/etc/dnsmasq.conf
sudo brew services start dnsmasq
sudo bash -c 'echo "nameserver 127.0.0.1" > /etc/resolver/loc'
```

This will allow anything with a .loc domain to point to the Traeffik proxy


# Usage

Instead of `docker-compose up -d` use `./develop up -d`. This will create a network called `ouroboros_default` which will make linking from other projects easier.