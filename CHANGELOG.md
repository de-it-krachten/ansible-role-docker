## [1.11.1](https://github.com/de-it-krachten/ansible-role-docker/compare/v1.11.0...v1.11.1) (2023-09-08)


### Bug Fixes

* Fix loop label to string ([9b08c60](https://github.com/de-it-krachten/ansible-role-docker/commit/9b08c60db4976eb43cd096311b43d7e961762043))

# [1.11.0](https://github.com/de-it-krachten/ansible-role-docker/compare/v1.10.1...v1.11.0) (2023-08-14)


### Features

* Update supported platforms & CI ([24318f9](https://github.com/de-it-krachten/ansible-role-docker/commit/24318f9a48994ab114059c5a2e0c4576aee93542))

## [1.10.1](https://github.com/de-it-krachten/ansible-role-docker/compare/v1.10.0...v1.10.1) (2023-08-13)


### Bug Fixes

* Implement proxy settings removal ([439ebb1](https://github.com/de-it-krachten/ansible-role-docker/commit/439ebb16f57b370e3ffabb028707a40a17650c7a))

# [1.10.0](https://github.com/de-it-krachten/ansible-role-docker/compare/v1.9.0...v1.10.0) (2023-07-07)


### Features

* Add proxy support ([2768bfd](https://github.com/de-it-krachten/ansible-role-docker/commit/2768bfd9348800f09a40974145a7c29894bb0861))
* Add support for SLES/OpenSUSE Leap 15 ([f2b80bb](https://github.com/de-it-krachten/ansible-role-docker/commit/f2b80bbfc8ae0601d9f441778e62bb0220ffec42))

# [1.9.0](https://github.com/de-it-krachten/ansible-role-docker/compare/v1.8.0...v1.9.0) (2023-06-28)


### Features

* Add support for LVM based volumes ([f9c50c1](https://github.com/de-it-krachten/ansible-role-docker/commit/f9c50c16bc0f92304171ef10b575aea10238df6c))

# [1.8.0](https://github.com/de-it-krachten/ansible-role-docker/compare/v1.7.1...v1.8.0) (2023-06-25)


### Features

* Move scripts to docker_scripts role ([6a6a251](https://github.com/de-it-krachten/ansible-role-docker/commit/6a6a251f22ac98f93f871566c25d12896945d8b0))

## [1.7.1](https://github.com/de-it-krachten/ansible-role-docker/compare/v1.7.0...v1.7.1) (2023-06-06)


### Bug Fixes

* Fix warnings from backup/restore scripts ([e4526aa](https://github.com/de-it-krachten/ansible-role-docker/commit/e4526aa0419e178f50865f9f0f48c491c414149b))

# [1.7.0](https://github.com/de-it-krachten/ansible-role-docker/compare/v1.6.2...v1.7.0) (2023-05-06)


### Features

* Add restore script for docker-compose backup ([07412eb](https://github.com/de-it-krachten/ansible-role-docker/commit/07412eb6b0f6317cb0600b98bd52f4ee3f378bb2))

## [1.6.2](https://github.com/de-it-krachten/ansible-role-docker/compare/v1.6.1...v1.6.2) (2023-04-10)


### Bug Fixes

* Change how task files are included to work around lint issue ([28e7797](https://github.com/de-it-krachten/ansible-role-docker/commit/28e7797b40bbb26bf4fc36138879abae8a5556d2))
* Move APT signing key to '/etc/trusted.gpg.d' location ([4896b25](https://github.com/de-it-krachten/ansible-role-docker/commit/4896b25ae110ff68db84bfd852f04a49374066de))

## [1.6.1](https://github.com/de-it-krachten/ansible-role-docker/compare/v1.6.0...v1.6.1) (2022-12-31)


### Bug Fixes

* Change how task files are included to work around lint issue ([809ae85](https://github.com/de-it-krachten/ansible-role-docker/commit/809ae85c088c467b473f03c0aaf038a95a234e71))
* Fix faulty package name for Fedora ([dd3b9cd](https://github.com/de-it-krachten/ansible-role-docker/commit/dd3b9cd28bff6f5b6f42046b03739461b9ec0222))

# [1.6.0](https://github.com/de-it-krachten/ansible-role-docker/compare/v1.5.0...v1.6.0) (2022-11-27)


### Features

* Add scripts for backup & cleanup ([8641386](https://github.com/de-it-krachten/ansible-role-docker/commit/8641386571e62a205326852b9b1c41076db61337))

# [1.5.0](https://github.com/de-it-krachten/ansible-role-docker/compare/v1.4.1...v1.5.0) (2022-11-17)


### Features

* Add support for OracleLinux 9 ([e6f6586](https://github.com/de-it-krachten/ansible-role-docker/commit/e6f6586928dacf21395412ba066c337c34682dfc))

## [1.4.1](https://github.com/de-it-krachten/ansible-role-docker/compare/v1.4.0...v1.4.1) (2022-10-23)


### Bug Fixes

* rename automatic file naming for apt source ([b4da1bd](https://github.com/de-it-krachten/ansible-role-docker/commit/b4da1bd1fde87101ce2730e8e94364c0af87d39a))

# [1.4.0](https://github.com/de-it-krachten/ansible-role-docker/compare/v1.3.0...v1.4.0) (2022-10-12)


### Features

* Add support for other architecture than 'x86_64' ([d1a6121](https://github.com/de-it-krachten/ansible-role-docker/commit/d1a61219dfe7c1480213a154e55e261564776177))
* Move to FQCN ([47cf590](https://github.com/de-it-krachten/ansible-role-docker/commit/47cf590b57cd36420004722055be5e3fa3213b79))
* Update CI to latest standards ([586f649](https://github.com/de-it-krachten/ansible-role-docker/commit/586f64998dac37fd58271a3ac27616c81403982b))

# [1.3.0](https://github.com/de-it-krachten/ansible-role-docker/compare/v1.2.3...v1.3.0) (2022-07-28)


### Features

* Implement ansible-lint v6 support ([aa3d09c](https://github.com/de-it-krachten/ansible-role-docker/commit/aa3d09c6bd83573e3daf3ecbefae526492e17a47))

## [1.2.3](https://github.com/de-it-krachten/ansible-role-docker/compare/v1.2.2...v1.2.3) (2022-06-28)


### Bug Fixes

* disable cgroups v2 on Fedora (again) ([924d79e](https://github.com/de-it-krachten/ansible-role-docker/commit/924d79e90b9933b7e48433857a2868a0a467576b))

## [1.2.2](https://github.com/de-it-krachten/ansible-role-docker/compare/v1.2.1...v1.2.2) (2022-06-27)


### Bug Fixes

* Remove disabling of cgroups v2 on Fedora ([e910976](https://github.com/de-it-krachten/ansible-role-docker/commit/e91097688ff7585c8d19d8e8cc7d78fe27d2ae08))

## [1.2.1](https://github.com/de-it-krachten/ansible-role-docker/compare/v1.2.0...v1.2.1) (2022-05-31)


### Bug Fixes

* API only started when requested ([36a3f82](https://github.com/de-it-krachten/ansible-role-docker/commit/36a3f826581ed77598e64ece6c514c333e14fc01))

# [1.2.0](https://github.com/de-it-krachten/ansible-role-docker/compare/v1.1.1...v1.2.0) (2022-05-10)


### Bug Fixes

* remove obsolete roles from meta/requirements.yml ([d09dc46](https://github.com/de-it-krachten/ansible-role-docker/commit/d09dc46f2ff706d0e67cd5d22528097cbbb9df73))


### Features

* add support for Ubuntu 22.04 ([ea6b439](https://github.com/de-it-krachten/ansible-role-docker/commit/ea6b439dc1af1ed4921080b8f60e54f1662010d5))

## [1.1.1](https://github.com/de-it-krachten/ansible-role-docker/compare/v1.1.0...v1.1.1) (2022-04-02)


### Bug Fixes

* code fixes for API/TLS activation ([5c0566e](https://github.com/de-it-krachten/ansible-role-docker/commit/5c0566e98b1daf8d993ba1c4bce3cd213d306f11))

# [1.1.0](https://github.com/de-it-krachten/ansible-role-docker/compare/v1.0.0...v1.1.0) (2022-02-26)


### Features

* add support for networking from container to the outside world ([514191f](https://github.com/de-it-krachten/ansible-role-docker/commit/514191febf015a19cab7b86022ec6c17005aabc8))

# 1.0.0 (2022-01-15)


### Features

* initial release ([729469b](https://github.com/de-it-krachten/ansible-role-docker/commit/729469bd2cd48fe46b73f61c630447d539816eae))
