# balena-homelab

WORK IN PROGRESS - DO NOT USE

This project is a [balenaCloud](https://www.balena.io/cloud) stack with the following services:

* [Pihole](https://hub.docker.com/r/pihole/pihole)
* [Unbound](https://hub.docker.com/r/klutchell/unbound)
* [Cloudflared](https://hub.docker.com/r/klutchell/cloudflared)
* [DNSCrypt-proxy](https://hub.docker.com/r/klutchell/dnscrypt-proxy)
* [Traefik](https://hub.docker.com/_/traefik/)
* [Nextcloud](https://hub.docker.com/_/nextcloud/)
* [Smokeping](https://hub.docker.com/r/linuxserver/smokeping)
* [Raneto](https://hub.docker.com/r/linuxserver/raneto)
* [MariaDB](https://hub.docker.com/r/linuxserver/mariadb)
* [whoami](https://hub.docker.com/r/containous/whoami/)

## Getting Started

To get started you'll first need to sign up for a free balenaCloud account and flash your device.

<https://www.balena.io/docs/learn/getting-started>

## Deployment

Once your account is set up, deployment is carried out by downloading the project and pushing it to your device either via Git or the balena CLI.

### Application Environment Variables

Application envionment variables apply to all services within the application, and can be applied fleet-wide to apply to multiple devices.

|Name|Example|Purpose|
|---|---|---|
|`TZ`|`America/Toronto`|(optional) inform services of the [timezone](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones) in your location|
|`CF_API_EMAIL`|`foo@bar.com`|(required) cloudflare account email|
|`CF_API_KEY`|`b9841238feb177a84330febba8a83208921177bffe733`|(required) cloudflare global API key|
|`TRAEFIK_CERTIFICATESRESOLVERS_CLOUDFLARE_ACME_EMAIL`|`foo@bar.com`|(required) email address for ACME registration|
|`TRAEFIK_LOG_LEVEL`|`DEBUG`|(optional) log level for traefik|
|`TRAEFIK_CERTIFICATESRESOLVERS_CLOUDFLARE_ACME_CASERVER`|`https://acme-staging-v02.api.letsencrypt.org/directory`|(optional) specify a different CA server to use|
|`WEBPASSWORD`|`mysecretpassword`|(optional) password for accessing the web-based interface of Pi-hole|

## Usage

### basic auth

Connect to the traefik service and run the following:

```bash
apk add --no-cache apache2-utils
htpasswd -c /etc/traefik/.htpasswd <username>
```

## Contributing

Please open an issue or submit a pull request with any features, fixes, or changes.

## Author

Kyle Harding <https://klutchell.dev>

## Acknowledgments

I didn't create any of these docker images myself, so credit goes to the
image maintainers, and the original software creators.

## License

[MIT License](./LICENSE)
