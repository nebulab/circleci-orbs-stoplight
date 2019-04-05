# Stoplight CircleCI Orb

[stoplight](https://circleci.com/orbs/registry/orb/nebulab/stoplight)

## Description

This Orb can be used to publish your API documentation to [Stoplight](https://stoplight.io) as part
of your CI process.

## Usage

Add the following to your CircleCI configuration:

```yaml
version: 2.1

orbs:
  stoplight: nebulab/stoplight

workflows:
  cool-workflow:
    jobs:
      - stoplight/push:
          organization: your-stoplight-org
          project: your-stoplight-project
          git_token: $STOPLIGHT_GIT_TOKEN
          source_dir: stoplight-contents-dir
          username: $STOPLIGHT_USERNAME
      - stoplight/publish:
          api_token: $STOPLIGHT_API_TOKEN
          domain: your-site.docs.stoplight.io
          requires:
            - stoplight/push
```

Then set the `STOPLIGHT_USERNAME`, `STOPLIGHT_API_TOKEN` and `STOPLIGHT_GIT_TOKEN` environment
variables (this is sensitive information so it shouldn't go in your `.circleci/config.yml`).

## Publishing

The [orb-tools Orb](https://github.com/CircleCI-Public/orb-tools-orb) is used for publishing
development and production versions of this Orb.

## Contributing

Bug reports and pull requests are welcome!

## License

circleci-orbs-stoplight is copyright © 2019 [Nebulab](http://nebulab.it/). It is free software, and
may be redistributed under the terms specified in the [CircleCI Orbs License](https://circleci.com/orbs/registry/licensing).

## About

![Nebulab](http://nebulab.it/assets/images/public/logo.svg)

circleci-orbs-stoplight is funded and maintained by the [Nebulab](http://nebulab.it/) team.

We firmly believe in the power of open-source. [Contact us](http://nebulab.it/contact-us/) if you
like our work and you need help with your project design or development.
