# Mozilla’s Sync Server for Yunohost

The Sync Server provides a replacement for Firefox’s default server (hosted at Mozilla). Its code is available on [the Sync-1.5 Server documentation](https://docs.services.mozilla.com/howtos/run-sync-1.5.html) (no official documentation yet for the 1.6.x as it is really the bleeding edge version).

By default, a server set up will defer authentication to the Mozilla-hosted accounts server at [https://accounts.firefox.com](https://accounts.firefox.com). So you will still have to authenticate at Mozilla, but _the storage of your information will be done on your host_.

**Shipped version:** 1.6.2

## Configuring

Once installed, reaching `http://domain.tld/path` should show a page explaining how to configure it. Otherwise please refer to the [Yunohost page](https://yunohost.org/#/app_ffsync).

## Contributing

From the `sources` directory, do as follows:

`make build`

`make test`

`./local/bin/gunicorn --reload --paste syncserver.ini` instead of the classical `make serve` to take into account changes you will surely do by developping the app.
