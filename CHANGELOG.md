# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
[markdownlint](https://dlaa.me/markdownlint/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

-
## [1.1.8] - 2024-03-??

### Changed in 1.1.8

- removed stream-loader and queues
- Updated to Senzing 3.9.0
- updated docker images

## [1.1.7] - 2023-06-30

### Changed in 1.1.7

- Updated to Senzing 3.6.0
- updated docker images

## [1.1.6] - 2023-06-26

### Changed in 1.1.6

- Updated to Senzing 3.5.3
- updated docker images

## [1.1.5] - 2023-05-12

### Changed in 1.1.5

- Updated to Senzing 3.5.2
- updated docker images

## [1.1.3] - 2023-01-17

### Changed in 1.1.3

- Updated to Senzing 3.4.0
- Updated database parameters

## [1.1.2] - 2022-10-13

### Changed in 1.1.2

- Updated to Senzing 3.3.1

## [1.1.1] - 2022-09-30

### Changed in 1.1.1

- Updated to Senzing 3.3.0

## [1.1.0] - 2022-09-15

### Changed in 1.1.0

- No further need for EFS, remove it
- map version selection to list of images
- Senzing License as environment variable #98
- Update to Senzing v3.2 #107
- Remove initContainer
- Remove EcsTaskDefinitionInstallSenzing
- Remove Apt image
- Update database version #109
- Update to be web-app-demo #111

## [1.0.12] - 2022-07-29

### Changed in 1.0.12

- added SecondsBeforeTimeout setting
- updated to support different engine config depending on database config
- updated how we output image versions.  there is apparently a new restriction: "Cannot export output ImageVersions with length 1205. Max length of 1024 exceeded."

## [1.0.11] - 2022-06-13

### Changed in 1.0.11

- updated resource names to allow for 21 char stack names
- updated readme to reflect stack name character limit
- updated readme to include additional text.
- added image versions to stack output
- changed UserPoolDomain to include random suffix
- updated to Senzing version 3.1.0
- updated Docker images to latest stable

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
