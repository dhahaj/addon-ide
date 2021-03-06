# Community Hass.io Add-ons: IDE

[![GitHub Release][releases-shield]][releases]
![Project Stage][project-stage-shield]
![Project Maintenance][maintenance-shield]
[![GitHub Activity][commits-shield]][commits]
[![License][license-shield]](LICENSE.md)

[![CircleCI][circleci-shield]][circleci]
[![Code Climate][codeclimate-shield]][codeclimate]
[![Bountysource][bountysource-shield]][bountysource]
[![Discord][discord-shield]][discord]
[![Community Forum][forum-shield]][forum]

[![Patreon][patreon-shield]][patreon]
[![PayPal][paypal-shield]][paypal]
[![Bitcoin][bitcoin-shield]][bitcoin]

Advanced IDE for Home Assistant, based on Cloud9 IDE

## WARNING

This add-on is currently in a **HIGHLY EXPERIMENTAL** state and under
active development.

## About

Cloud9 IDE is an online integrated development environment. It supports
hundreds of programming languages, including C, C++, PHP, Ruby, Perl, Python,
JavaScript with Node.js, and Go.

This add-on is a packaged version of the Cloud9 IDE, tuned for use with Home
Assistant. It is designed to allow you to configure and edit your Home Assistant
setup straight from the web interface using a useful, pretty and fullblown
editor.

![IDE in the Home Assistant Frontend](images/screenshot.png)

## Installation

The installation of this add-on is pretty straightforward and not different in
comparison to installing any other Hass.io add-on.

1. [Add our Hass.io add-ons repository][repository] to your Hass.io instance.
1. Install the "IDE" add-on.
1. Start the "IDE" add-on
1. Check the logs of the "IDE" add-on to see if everything went well.
1. Surf to your Hass.io instance and use port `8321`
    (e.g. `http://hassio.local:8321`).

**NOTE**: Do not add this repository to Hass.io, please use:
`https://github.com/hassio-addons/repository`.

## Docker status

[![Docker Architecture][armhf-arch-shield]][armhf-dockerhub]
[![Docker Version][armhf-version-shield]][armhf-microbadger]
[![Docker Layers][armhf-layers-shield]][armhf-microbadger]
[![Docker Pulls][armhf-pulls-shield]][armhf-dockerhub]

[![Docker Architecture][aarch64-arch-shield]][aarch64-dockerhub]
[![Docker Version][aarch64-version-shield]][aarch64-microbadger]
[![Docker Layers][aarch64-layers-shield]][aarch64-microbadger]
[![Docker Pulls][aarch64-pulls-shield]][aarch64-dockerhub]

[![Docker Architecture][amd64-arch-shield]][amd64-dockerhub]
[![Docker Version][amd64-version-shield]][amd64-microbadger]
[![Docker Layers][amd64-layers-shield]][amd64-microbadger]
[![Docker Pulls][amd64-pulls-shield]][amd64-dockerhub]

[![Docker Architecture][i386-arch-shield]][i386-dockerhub]
[![Docker Version][i386-version-shield]][i386-microbadger]
[![Docker Layers][i386-layers-shield]][i386-microbadger]
[![Docker Pulls][i386-pulls-shield]][i386-dockerhub]

## Configuration

**Note**: _Remember to restart the add-on when the configuration is changed._

Example add-on configuration:

```json
{
  "log_level": "info",
  "username": "hassio",
  "password": "changeme",
  "ssl": true,
  "certfile": "fullchain.pem",
  "keyfile": "privkey.pem",
  "packages": [
    "php7-cli"
  ],
  "init_commands": []
}
```

**Note**: _This is just an example, don't copy and past it! Create your own!_

### Option: `log_level`

The `log_level` option controls the level of log output by the addon and can
be changed to be more or less verbose, which might be useful when you are
dealing with an unknown issue. Possible values are:

- `trace`: Show every detail, like all called internal functions.
- `debug`: Shows detailed debug information.
- `info`: Normal (usually) interesting events.
- `warning`: Exceptional occurrences that are not errors.
- `error`:  Runtime errors that do not require immediate action.
- `fatal`: Something went terribly wrong. Add-on becomes unusable.

Please note that each level automatically includes log messages from a
more severe level, e.g., `debug` also shows `info` messages. By default,
the `log_level` is set to `info`, which is the recommended setting unless
you are troubleshooting.

Using `trace` or `debug` log levels puts the cloud9 server into debug mode
as well.

### Option: `username`

This option allows you to enable authentication on accessing the IDE. Leaving
it empty would disable the possibility to authenticate completely.

**Note**: _If you set an `username`, `password` becomes mandatory as well._

### Option: `password`

Sets the password to authenticate with. Leaving it empty would disable the
possibility to authenticate completely.

**Note**: _If you set a `password`, `username` becomes mandatory as well._

### Option: `ssl`

Enables/Disables SSL (HTTPS) on the IDE. Set it `true` to enable it,
`false` otherwise.

### Option: `certfile`

The certificate file to use for SSL.

**Note**: _The file MUST be stored in `/ssl/`, which is default for Hass.io_

### Option: `keyfile`

The private key file to use for SSL.

**Note**: _The file MUST be stored in `/ssl/`, which is default for Hass.io_

### Option: `packages`

Allows you to specify additional [Alpine packages][alpine-packages] to be
installed in your shell environment (e.g., Python, PHP, Go).

**Note**: _Adding many packages will result in a longer start-up
time for the add-on._

### Option: `init_commands`

Customize your IDE environment even more with the `init_commands` option.
Add one or more shell commands to the list, and they will be executed every
single time this add-on starts.

## Embedding into Home Assistant

It is possible to embed the IDE directly into Home Assistant, allowing
you to access your IDE through the Home Assistant frontend.

Home Assistant provides the `panel_iframe` component, for these purposes.

Example configuration:

```yaml
panel_iframe:
  ide:
    title: IDE
    icon: mdi:code-braces
    url: https://addres.to.your.hass.io:8321
```

## Known issues and limitations

This add-on is currently in an experimental state, and some features are not
implemented yet. Some of the presently known limitations:

- User and project settings are not persistent between add-on restarts.
- Auto-completion is based on file contents and does not yet query Home
  Assistant.
- `ZSH` is available, but not enabled by default, due to Cloud9 limitations.

## Changelog & Releases

This repository keeps a [change log](CHANGELOG.md). The format of the log
is based on [Keep a Changelog][keepchangelog].

Releases are based on [Semantic Versioning][semver], and use the format
of ``MAJOR.MINOR.PATCH``. In a nutshell, the version will be incremented
based on the following:

- ``MAJOR``: Incompatible or major changes.
- ``MINOR``: Backwards-compatible new features and enhancements.
- ``PATCH``: Backwards-compatible bugfixes and package updates.

## Support

Got questions?

You have several options to get them answered:

- The Home Assistant [Community Forum][forum], we have a
  [dedicated topic][forum] on that forum regarding this repository.
- The Home Assistant [Discord Chat Server][discord] for general Home Assistant
  discussions and questions.
- Join the [Reddit subreddit][reddit] in [/r/homeassistant][reddit]

You could also [open an issue here][issue] GitHub.

## Contributing

This is an active open-source project. We are always open to people who want to
use the code or contribute to it.

We have set up a separate document containing our
[contribution guidelines](CONTRIBUTING.md).

Thank you for being involved! :heart_eyes:

## Authors & contributors

The original setup of this repository is by [Franck Nijhof][frenck].

For a full list of all authors and contributors,
check [the contributor's page][contributors].

## We have got some Hass.io add-ons for you

Want some more functionality to your Hass.io Home Assistant instance?

We have created multiple add-ons for Hass.io. For a full list, check out
our [GitHub Repository][repository].

## License

MIT License

Copyright (c) 2017 Franck Nijhof

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

[aarch64-arch-shield]: https://img.shields.io/badge/architecture-aarch64-blue.svg
[aarch64-dockerhub]: https://hub.docker.com/r/hassioaddons/ide-aarch64
[aarch64-layers-shield]: https://images.microbadger.com/badges/image/hassioaddons/ide-aarch64.svg
[aarch64-microbadger]: https://microbadger.com/images/hassioaddons/ide-aarch64
[aarch64-pulls-shield]: https://img.shields.io/docker/pulls/hassioaddons/ide-aarch64.svg
[aarch64-version-shield]: https://images.microbadger.com/badges/version/hassioaddons/ide-aarch64.svg
[alpine-packages]: https://pkgs.alpinelinux.org/packages
[amd64-arch-shield]: https://img.shields.io/badge/architecture-amd64-blue.svg
[amd64-dockerhub]: https://hub.docker.com/r/hassioaddons/ide-amd64
[amd64-layers-shield]: https://images.microbadger.com/badges/image/hassioaddons/ide-amd64.svg
[amd64-microbadger]: https://microbadger.com/images/hassioaddons/ide-amd64
[amd64-pulls-shield]: https://img.shields.io/docker/pulls/hassioaddons/ide-amd64.svg
[amd64-version-shield]: https://images.microbadger.com/badges/version/hassioaddons/ide-amd64.svg
[armhf-arch-shield]: https://img.shields.io/badge/architecture-armhf-blue.svg
[armhf-dockerhub]: https://hub.docker.com/r/hassioaddons/ide-armhf
[armhf-layers-shield]: https://images.microbadger.com/badges/image/hassioaddons/ide-armhf.svg
[armhf-microbadger]: https://microbadger.com/images/hassioaddons/ide-armhf
[armhf-pulls-shield]: https://img.shields.io/docker/pulls/hassioaddons/ide-armhf.svg
[armhf-version-shield]: https://images.microbadger.com/badges/version/hassioaddons/ide-armhf.svg
[bitcoin-shield]: https://img.shields.io/badge/donate-bitcoin-blue.svg
[bitcoin]: https://blockchain.info/payment_request?address=3GVzgN6NpVtfXnyg5dQnaujtqVTEDBCtAH
[bountysource-shield]: https://img.shields.io/bountysource/team/hassio-addons/activity.svg
[bountysource]: https://www.bountysource.com/teams/hassio-addons/issues
[circleci-shield]: https://img.shields.io/circleci/project/github/hassio-addons/addon-ide.svg
[circleci]: https://circleci.com/gh/hassio-addons/addon-ide
[codeclimate-shield]: https://img.shields.io/badge/code%20climate-protected-brightgreen.svg
[codeclimate]: https://codeclimate.com/github/hassio-addons/addon-ide
[commits-shield]: https://img.shields.io/github/commit-activity/y/hassio-addons/addon-ide.svg
[commits]: https://github.com/hassio-addons/addon-ide/commits/master
[contributors]: https://github.com/hassio-addons/addon-ide/graphs/contributors
[discord-shield]: https://img.shields.io/discord/330944238910963714.svg
[discord]: https://discord.gg/c5DvZ4e
[forum-shield]: https://img.shields.io/badge/community-forum-brightgreen.svg
[forum]: https://community.home-assistant.io/t/repository-community-hass-io-add-ons/24705?u=frenck
[frenck]: https://github.com/frenck
[home-assistant]: https://home-assistant.io
[i386-arch-shield]: https://img.shields.io/badge/architecture-i386-blue.svg
[i386-dockerhub]: https://hub.docker.com/r/hassioaddons/ide-i386
[i386-layers-shield]: https://images.microbadger.com/badges/image/hassioaddons/ide-i386.svg
[i386-microbadger]: https://microbadger.com/images/hassioaddons/ide-i386
[i386-pulls-shield]: https://img.shields.io/docker/pulls/hassioaddons/ide-i386.svg
[i386-version-shield]: https://images.microbadger.com/badges/version/hassioaddons/ide-i386.svg
[issue]: https://github.com/hassio-addons/addon-ide/issues
[keepchangelog]: http://keepachangelog.com/en/1.0.0/
[license-shield]: https://img.shields.io/github/license/hassio-addons/addon-ide.svg
[maintenance-shield]: https://img.shields.io/maintenance/yes/2017.svg
[ohmyzsh]: http://ohmyz.sh/
[patreon-shield]: https://img.shields.io/badge/donate-patreon-blue.svg
[patreon]: https://www.patreon.com/frenck
[paypal-shield]: https://img.shields.io/badge/donate-paypal-blue.svg
[paypal]: https://www.paypal.me/FranckNijhof
[project-stage-shield]: https://img.shields.io/badge/project%20stage-experimental-yellow.svg
[reddit]: https://reddit.com/r/homeassistant
[releases-shield]: https://img.shields.io/github/release/hassio-addons/addon-ide.svg
[releases]: https://github.com/hassio-addons/addon-ide/releases
[repository]: https://github.com/hassio-addons/repository
[semver]: http://semver.org/spec/v2.0.0.htm
[zsh]: https://en.wikipedia.org/wiki/Z_shell
