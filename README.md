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
      go-production:
        docker:
          - image: circleci/ruby
        steps:
          - stoplight/publish:  
              organization: your-stoplight-org
              project: your-stoplight-project
              username: $STOPLIGHT_USERNAME
              api_token: $STOPLIGHT_API_TOKEN
              git_token: $STOPLIGHT_GIT_TOKEN
              source_dir: stoplight-contents-dir
              domain: your-site.docs.stoplight.io
```

Then set the `STOPLIGHT_USERNAME`, `STOPLIGHT_API_TOKEN` and `STOPLIGHT_GIT_TOKEN` environment
variables (this is sensitive information so it shouldn't go in your `.circle.yml`).

## Publish on Orbs Registry

To publish CircleCI Orbs we use GitHub Actions configured under `.github` folder. Here's how to
release an Orb, both for production and development.

### Production Release

To publish a new version it's just needed to [create a new release for this repository](https://github.com/nebulab/circleci-orbs-stoplight/releases).
A GitHub action will take care of everything else.

**NOTE:** The release tag name should match what CircleCI Orbs Registry expects, so:

- `1.5.0` :thumbsup:
- `v1.2` :thumbsdown:

### Development Release

Every time you push a commit into master or any other branch, a GitHub Action will be triggered to
release a development version of the Orb, scoped by branch name.

For example if you push a commit to the `your-username/my-feature` branch, a new development orb
will be published as `nebulab/stoplight@dev:your-username-my-feature`.

**NOTE:** Development orbs are mutable and expire after 90 days. If someone else pushes a new commit
on the same branch your development orb will be overwritten.

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
