# balena-homelab

WORK IN PROGRESS - DO NOT USE

This project is a [balenaCloud](https://www.balena.io/cloud) stack with the following services:

- [raneto](https://hub.docker.com/r/linuxserver/raneto)
- [smokeping](https://hub.docker.com/r/linuxserver/smokeping)
- [whoami](https://hub.docker.com/r/containous/whoami/)
- [duplicati](https://hub.docker.com/r/linuxserver/duplicati)
- [traefik](https://hub.docker.com/_/traefik/)
- ~~[pihole](https://hub.docker.com/r/pihole/pihole)~~
- ~~[unbound](https://hub.docker.com/r/klutchell/unbound)~~
- ~~[cloudflared](https://hub.docker.com/r/klutchell/cloudflared)~~
- ~~[dnscrypt-proxy](https://hub.docker.com/r/klutchell/dnscrypt-proxy)~~
- ~~[nextcloud](https://hub.docker.com/_/nextcloud/)~~
- ~~[mariadb](https://hub.docker.com/r/linuxserver/mariadb)~~

## Getting Started

To get started you'll first need to sign up for a free balenaCloud account and flash your device.

<https://www.balena.io/docs/learn/getting-started>

## Deployment

Once your account is set up, deployment is carried out by downloading the project and pushing it to your device either via Git or the balena CLI.

### Application Environment Variables

Application envionment variables apply to all services within the application, and can be applied fleet-wide to apply to multiple devices.

- `TZ` - (optional) inform services of the [timezone](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones) in your location (eg. `America/Toronto`)
- `CF_API_EMAIL` - (required) cloudflare account email (eg. `foo@bar.com`)
- `CF_API_KEY` - (required) cloudflare global API key (eg. `b9841238feb177a84330febba8a83208921177bffe733`)
- `TRAEFIK_CERTIFICATESRESOLVERS_CLOUDFLARE_ACME_EMAIL` - (required) email address for ACME registration (eg. `foo@bar.com`)
- `TRAEFIK_LOG_LEVEL` - (optional) log level for traefik (eg. `DEBUG`)
- `TRAEFIK_CERTIFICATESRESOLVERS_CLOUDFLARE_ACME_CASERVER` - (optional) specify a different CA server to use (eg. `https://acme-staging-v02.api.letsencrypt.org/directory`)
- `TRAEFIK_PROVIDERS_DOCKER_DEFAULTRULE` - (required) Replace mydomain.com with your domain managed by Cloudflare (eg. ``Host(`{{index .Labels "subdomain"}}.mydomain.com`)``)
- ~~`WEBPASSWORD` - (optional) password for accessing the web-based interface of Pi-hole (eg. `mysecretpassword`)~~

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
