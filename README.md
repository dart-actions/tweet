[![GitHub Sponsor](https://img.shields.io/static/v1?label=Sponsor&message=%E2%9D%A4&logo=GitHub&color=ff69b4)](https://github.com/sponsors/myConsciousness)
[![GitHub Sponsor](https://img.shields.io/static/v1?label=Maintainer&message=myConsciousness&logo=GitHub&color=00acee)](https://github.com/myConsciousness)

[![v2](https://img.shields.io/endpoint?url=https%3A%2F%2Ftwbadges.glitch.me%2Fbadges%2Fv2)](https://developer.twitter.com/en/docs/twitter-api)
[![Powered by twitter_api_v2](https://img.shields.io/badge/Powered%20by-twitter_api_v2-00acee.svg)](https://github.com/twitter-dart/twitter-api-v2)

# Send a tweet from a GitHub Actions workflow

Use this action to send a tweet from a GitHub actions workflow.

This action is implemented in the Dart language and uses [twitter_api_v2](https://github.com/twitter-dart/twitter-api-v2) for tweeting.

> Note:</br>
> This project is inspired by [send-tweet-action](https://github.com/ethomson/send-tweet-action) created by [@ethomson](https://github.com/ethomson).</br>

## Twitter Application Setup

First, you'll need to create a Twitter application if you haven't
already.  This will allow you to programmatically authenticate to
the Twitter API and send a tweet.

If you haven't already, visit
[developer.twitter.com/apps](https://developer.twitter.com/apps)
and create a Twitter application.  Then create keys and tokens
to use for authentication.

## Secret Configuration

Configure the authentication keys and tokens for your Twitter
app as secrets in your repository.  I recommend using the `TWITTER_BEARER_TOKEN`,
`TWITTER_CONSUMER_KEY`, `TWITTER_CONSUMER_SECRET`,
`TWITTER_ACCESS_TOKEN`, and `TWITTER_ACCESS_TOKEN_SECRET`
secrets.

## Workflow Usage

Configure your workflow to use `dart-actions/tweet@v0.0.1`,
and provide the tweet you want to send as the `status` input.

Provide the authentication keys and tokens for your Twitter app
as the `consumer-key`, `consumer-secret`, `access-token`, and
`access-token-secret` inputs.

For example:

```yml
name: Send a Tweet

on:
    [push]

jobs:
  tweet:
    runs-on: ubuntu-latest
    steps:
      - uses: dart-actions/tweet@v0.0.1
        with:
          text: "Hello, World!"
          consumer-key: ${{ secrets.TWITTER_CONSUMER_KEY }}
          consumer-secret: ${{ secrets.TWITTER_CONSUMER_SECRET }}
          access-token: ${{ secrets.TWITTER_ACCESS_TOKEN }}
          access-token-secret: ${{ secrets.TWITTER_ACCESS_TOKEN_SECRET }}
```

Or, you can use access token issued by OAuth 2.0 PKCE as `bearer-token`.

```yml
name: Send a Tweet

on:
    [push]

jobs:
  tweet:
    runs-on: ubuntu-latest
    steps:
      - uses: dart-actions/tweet@v0.0.1
        with:
          text: "Hello, World!"
          bearer-token: ${{ secrets.TWITTER_BEARER_TOKEN }}
```

Now whenever you push something to your repository, GitHub Actions
will tweet on your behalf.
