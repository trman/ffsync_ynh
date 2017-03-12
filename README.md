# Mozilla’s Sync Server for Yunohost
<p align="left">
        <img src="https://img.shields.io/badge/status-working-green.svg"
             alt="yunohost status">
</p>

The Sync Server (ex Weaver) provides a replacement for Firefox’s default server (hosted at Mozilla). Its code is available on [the Sync-1.5 Server documentation](https://docs.services.mozilla.com/howtos/run-sync-1.5.html) (no official documentation yet for the 1.6.x as it is really the bleeding edge version).

By default, a server set up will defer authentication to the Mozilla-hosted accounts server at [https://accounts.firefox.com](https://accounts.firefox.com). So you will still have to authenticate at Mozilla, but _the storage of your information will be done on your host_.

**Shipped Sync Server version:** 1.6.2 (still 1.5 API)

## Getting Started

Install it with the current url via the admin interface, or for a verbose install using `sudo yunohost app install https://github.com/YunoHost-Apps/ffsync_ynh --verbose`.

Once installed, reaching `http://domain.tld/path/` should show a page explaining how to configure it. Otherwise please refer to the [Yunohost page](https://yunohost.org/#/app_ffsync).

<p align="center">
        <img src="https://cloud.githubusercontent.com/assets/6329880/23835111/c6e20640-0761-11e7-8f07-00e76198ac6b.png"
             alt="welcoming page">
</p>

## Contributing

From the `sources` directory, do as follows:

`make build`

`make test`

`./local/bin/gunicorn --reload --paste syncserver.ini` instead of the classical `make serve` to take into account changes you will surely do by developping the app.

## Debug

Apart from the typical `service ffsync status`, you might want to see what requests cause errors by coloring them:

```bash
tail -f /var/log/ffsync.log | perl -pe 's/.*404.*/\e[1;31m$&\e[0m/g'
```
