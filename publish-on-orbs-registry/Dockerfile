FROM circleci/circleci-cli:alpine

LABEL "com.github.actions.name"="Publish Orb on CircleCI Registry"
LABEL "com.github.actions.description"="Publish Orb on CircleCI Registry"
LABEL "com.github.actions.icon"="mic"
LABEL "com.github.actions.color"="black"

LABEL "repository"="http://github.com/nebulab/circleci-orbs-stoplight"
LABEL "homepage"="http://github.com/nebulab/circleci-orbs-stoplight"
LABEL "maintainer"="kennyadsl <kennyadsl@gmail.com>"

ADD entrypoint.sh /entrypoint.sh
ENTRYPOINT ["/entrypoint.sh"]
