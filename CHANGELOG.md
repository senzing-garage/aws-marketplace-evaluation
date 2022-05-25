# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
[markdownlint](https://dlaa.me/markdownlint/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

- updated resource names to allow for 21 char stack names
- updated readme to reflect stack name character limit
- updated readme to include additional text.

## [1.0.10] - 2022-05-20

### Changed in 1.0.10

- no changes, release created to test automation

## [1.0.9] - 2022-05-13

### Changed in 1.0.9

- update images to 3.0.0
- update Senzing version to 3.0.0
- migrated from yum to apt installer
- remove "-withinfo" for loader and redoer
- update dashboards
- update to 3.0.0 paths
- add new truth set
- create new truth set data sources
- update certificate python to 3.8 and add `-1.0.2` to the filename `self-signed-certificate.zip`
- redoer queue parameters: ApplicationAutoScalingScalingPolicyRedoerLoader targetValue = 20
- add private API server URL
## [1.0.7] - 2022-03-10

### Changed in 1.0.7

- Removed Jupyter
- removed flowlogs
- updated image versions

## [1.0.6] - 2022-02-01

### Changed in 1.0.6

- updated to new yum image

## [1.0.5] - 2021-11-02

### Changed in 1.0.5

- extended subnets

## [1.0.4] - 2021-10-25

### Changed in 1.0.4

- Added XTERM env var

## [1.0.3] - 2021-10-15

### Changed in 1.0.3

- Updated versions of docker images

## [1.0.2] - 2021-10-08

### Changed in 1.0.2

- Updated policy to allow pulling images from private ECR

## [1.0.1] - 2021-10-05

### Changed in 1.0.1

- Updated lambda function error reporting


## [1.0.0] - 2021-09-10

### Changed in 1.0.0

- Initial version based on basic and database cluster
