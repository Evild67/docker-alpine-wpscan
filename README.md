[![Docker Stars](https://img.shields.io/docker/stars/evild/alpine-wpscan.svg?style=flat-square)](https://hub.docker.com/r/evild/alpine-wpscan/)
[![Docker Pulls](https://img.shields.io/docker/pulls/evild/alpine-wpscan.svg?style=flat-square)](https://hub.docker.com/r/evild/alpine-wpscan/)
[![ImageLayers Size](https://img.shields.io/imagelayers/image-size/evild/alpine-wpscan/latest.svg?style=flat-square)](https://hub.docker.com/r/evild/alpine-wpscan/)

# Alpine WPScan

This image is based on [evild/alpine-ruby](https://hub.docker.com/r/evild/alpine-ruby/)

## Version

- `latest` [(Dockerfile)](https://github.com/Evild67/docker-alpine-wpscan/blob/master/latest/Dockerfile)
- `2.9` [(Dockerfile)](https://github.com/Evild67/docker-alpine-wpscan/blob/master/release/Dockerfile)


## What is WPScan?
WPScan is a black box WordPress vulnerability scanner.

## Installation
Automated builds of the image are available on Dockerhub and is the recommended method of installation.
```
docker pull evild/alpine-wpscan:2.9
```
You can also pull the latest tag which is built from the repository HEAD. This build include HEAD from WPScan repository.
```
docker pull evild/alpine-wpscan:latest
```
Alternatively you can build the image locally.
```
docker build -t evild/alpine-wpscan github.com/evild67/alpine-wpscan
```

## Quick Start

The version of the database is the version available at the time of the build. It's recommended to update it before with **--update** argument.

```
docker run --rm evild/alpine-wpscan --update -u <http://website> [OPTIONS]
```

## WPScan Options

```
--update                            Update the database to the latest version.
--url       | -u <target url>       The WordPress URL/domain to scan.
--force     | -f                    Forces WPScan to not check if the remote site is running WordPress.
--enumerate | -e [option(s)]        Enumeration.
  option :
    u        usernames from id 1 to 10
    u[10-20] usernames from id 10 to 20 (you must write [] chars)
    p        plugins
    vp       only vulnerable plugins
    ap       all plugins (can take a long time)
    tt       timthumbs
    t        themes
    vt       only vulnerable themes
    at       all themes (can take a long time)
  Multiple values are allowed : "-e tt,p" will enumerate timthumbs and plugins
  If no option is supplied, the default is "vt,tt,u,vp"

--exclude-content-based "<regexp or string>"
                                    Used with the enumeration option, will exclude all occurrences based on the regexp or string supplied.
                                    You do not need to provide the regexp delimiters, but you must write the quotes (simple or double).
--config-file  | -c <config file>   Use the specified config file, see the example.conf.json.
--user-agent   | -a <User-Agent>    Use the specified User-Agent.
--cookie <String>                   String to read cookies from.
--random-agent | -r                 Use a random User-Agent.
--follow-redirection                If the target url has a redirection, it will be followed without asking if you wanted to do so or not
--batch                             Never ask for user input, use the default behaviour.
--no-color                          Do not use colors in the output.
--wp-content-dir <wp content dir>   WPScan try to find the content directory (ie wp-content) by scanning the index page, however you can specified it.
                                    Subdirectories are allowed.
--wp-plugins-dir <wp plugins dir>   Same thing than --wp-content-dir but for the plugins directory.
                                    If not supplied, WPScan will use wp-content-dir/plugins. Subdirectories are allowed
--proxy <[protocol://]host:port>    Supply a proxy. HTTP, SOCKS4 SOCKS4A and SOCKS5 are supported.
                                    If no protocol is given (format host:port), HTTP will be used.
--proxy-auth <username:password>    Supply the proxy login credentials.
--basic-auth <username:password>    Set the HTTP Basic authentication.
--wordlist | -w <wordlist>          Supply a wordlist for the password brute forcer.
--username | -U <username>          Only brute force the supplied username.
--usernames     <path-to-file>      Only brute force the usernames from the file.
--threads  | -t <number of threads> The number of threads to use when multi-threading requests.
--cache-ttl       <cache-ttl>       Typhoeus cache TTL.
--request-timeout <request-timeout> Request Timeout.
--connect-timeout <connect-timeout> Connect Timeout.
--max-threads     <max-threads>     Maximum Threads.
--throttle        <milliseconds>    Milliseconds to wait before doing another web request. If used, the --threads should be set to 1.
--help     | -h                     This help screen.
--verbose  | -v                     Verbose output.
--version                           Output the current version and exit.
```
