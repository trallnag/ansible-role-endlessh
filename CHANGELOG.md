# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html)
as well as the [Conventional Commits](https://www.conventionalcommits.org) 
specification.

## Unreleased

* Nothing

## [1.0.3] 2021-05-16

## Fixed

* Broken handler name.

## [1.0.2] 2021-05-16

## Changed

* Improved docs.
* Moved a few tasks to handlers.

## [1.0.1] 2021-05-16

## Changed

* Added pipefail flag to shell module and bin/bash to comply with Ansible
  linter `E306: Shells that use pipes should set the pipefail option`.
* Circumvent `E303: systemctl used in place of systemd module` by using alias.
  No other way. Systemd module does not support the reset-failed command.
* Add a bunch of skip lint tags.

## [1.0.0] 2021-05-16

* Intial release.

## Unreleased

* Nothing
