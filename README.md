Ouroboros
=====

A tool to make Docker-based development easier across multiple projects.

# Features

Ouroboros provides a small proxy that will allow you to use multiple Docker projects at once. In addition, it provides both [MailCatcher](https://mailcatcher.me/) and [Webgrind](https://github.com/jokkedk/webgrind) to help troubleshoot email issues (and prevent erroneous emails from being sent to customers) as well as to help profile performance and other issues with your PHP applications.

## Setting up DNS on Mac

For Mac we can use the `.test` top-level domain via [dnsmasq](http://www.thekelleys.org.uk/dnsmasq/doc.html) and [resolver](https://developer.apple.com/legacy/library/documentation/Darwin/Reference/ManPages/man5/resolver.5.html).

```
brew install dnsmasq
echo 'address=/.test/127.0.0.1' > /usr/local/etc/dnsmasq.conf
sudo brew services start dnsmasq
```

Check to make sure you have the directory `/etc/resolver`. If not, create it `sudo mkdir /etc/resolver`. Then you can add your `.test` resolver

```
sudo bash -c 'echo "nameserver 127.0.0.1" > /etc/resolver/test'
```

This will allow anything with a .test domain to point to the [Traefik](https://traefik.io/) proxy


# Usage

## Launching Ouroboros

Instead of `docker-compose up -d` use `./develop up -d`. This will create a network called `ouroboros_default` which will make linking from other projects easier.

## Accessing MailCatcher

To access MailCatcher simply point your browser to [http://mailcatcher.test]

## Accessing Webgrind

To access Webgrind simply point your browser to [http://webgrind.test]

## Access the Traefik dashboard

Traefik offers a great dashboard to help you visualize your sites. You can access it at [http://traefik.test:8080/dashboard/]
