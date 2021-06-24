# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html)
as well as the [Conventional Commits](https://www.conventionalcommits.org) 
specification.

## Unreleased

* Nothing

## [2.1.0] 2021-06-24

### Fixed

* Replaced setcap `cap_net_bind_service+ep` with `cap_net_bind_service=ep`. For
  some reason with `+ep` always changed status.

### Added

* Symlink `/usr/local/bin/endlessh -> /usr/bin/endlessh*` because this the
  path used in official service file.

### Changed

* Removed `---` from YAML files.
* Misc documentation.
* Copy official service file from
  <https://github.com/skeeto/endlessh/blob/master/util/endlessh.service>

## [2.0.2] 2021-06-03

### Added

* `DEVELOPMENT.md` to gather infos about development.

### Changed

* Switched to argument spec from assert file. Only supported starting with
  ansible-core 2.11. For more information, see here:
  <https://docs.ansible.com/ansible/latest/user_guide/playbooks_reuse_roles.html#role-argument-validation>.
* Simplified calling of handlers.
* Simplified error handling in shell task.

## [2.0.1] 2021-05-19

### Changed

* Replaced shell task with capabilties community module to set the flag that
  allows endlessh to listen on port 22.

## [2.0.0] 2021-05-19

### Added

* Asserts that test input.

### Changed

* **BREAKING CHANGE**: Removed absent feature.
* **BREAKING CHANGE**: Prefix all input variables with `endlessh_`.
* Switched license to Apache.

## [1.1.1] 2021-05-17

## Changed

* Replaced use of systemd module with shell script to stop and disable endlessh
  service if the service exists. The module fails if the service does not exist.

## [1.1.0] 2021-05-17

## Added

* Removal of init.d file if state is set to absent.

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
