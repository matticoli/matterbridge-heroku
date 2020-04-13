[![Code of Conduct](https://img.shields.io/badge/%E2%9D%A4-code%20of%20conduct-blue.svg?style=flat)](https://github.com/edgi-govdata-archiving/overview/blob/master/CONDUCT.md)

# Matterbridge-heroku

This is a fork of [the original
`matterbridge-heroku`](https://github.com/cadecairos/matterbridge-heroku).

It includes [a custom config file][config] specific to one implementation, but this can easily be modified in a new fork.

## About this Fork

[**Heroku**](https://www.heroku.com/what) is a platform for easily deploying
applications.

A [**buildpack**](https://docs.cloudfoundry.org/buildpacks/) provides
framework and runtime support for apps running on platforms like Heroku.

An [**_inline_ buildpack**](https://github.com/kr/heroku-buildpack-inline#readme) is a special buildpack that includes code for both the app and the
buildpack that _runs_ the app.

[**Matterbridge**](https://github.com/42wim/matterbridge#readme) is a
simple _bridge_ that can relay messages between a number of different
chat services, essentially connecting separate chat tools.

This fork is intended to help bridge channels between the WPI VEX U Slack and Discord for vexibot integration

* Required envvars:
  * `MATTERBRIDGE_VERSION`. Use a [matterbridge git tag][git-tags].
  * `SLACK_<team name>_TOKEN`. See [_Slack bot setup_ documentation][bot-setup].
  * `DISCORD_<server id>_TOKEN`.
* Optional envvars:
  * `MATTERBRIDGE_URL`. Use this to download the binary from a custom
    url instead of the tagged release from the official GitHub repo.
    (Setting this makes `MATTERBRIDGE_VERSION` ignored.)
    * With caution, you may want to use the [latest nightly matterbridge
      build](https://bintray.com/42wim/nightly/Matterbridge/_latestVersion)
      while waiting on the next official release.
  * `DEBUG`. Set to "1" to log all message events across bridges.
* Auto-deploys `master` branch to our heroku app: `matterbridge-vexu`
* Edit channel bridge config via [`config/config-heroku-template.toml`][config].

   [bot-setup]: https://github.com/42wim/matterbridge/wiki/Slack-bot-setup
   [git-tags]: https://github.com/42wim/matterbridge/tags
   [config]: config/config-heroku-template.toml
