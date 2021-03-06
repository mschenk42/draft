# Changelog

## v0.8.0

### Client

* implemented `draft delete` to remove applications from Kubernetes
* implemented `draft logs` to view build logs after `draft up`
* added --tail flag to `draft connect` (as well as `draft logs`)
* added -i/--image flag to `draft init` to override the draftd image
* added "upgrade" workflow to `draft init`
* installed the pack-repo plugin by default on `draft init`
* switched default listening port to 3000 for apps deployed with the default Ruby pack
* added global flag `--draft-namespace` for talking to draftd in another namespace

### Server

* bumped max RPC message size to 40MB

### Documentation

* clarified how to use ingress with the basedomain field
* added an asciicast on draft's workflow
* added documentation on creating and maintaining a pack repository

## v0.7.0

### Client

* introduced `draft connect`
* added a new UI for `draft up`
* introduced language aliases to linguist

### Server

* removed requirement for ingress setup, making it optional
* bumped GRPC max message size from 4MB to 20MB
* removed registry org and image name from generated charts, simplifying templates

### Community

* introduced a draft Homebrew formula. Use `brew tap azure/draft && brew install draft` to try it out

## v0.6.0

### Client

* introduced a new plugin manager! See `draft plugins`
* introduced smarter language detection for apps through `draft create`
* `draft init --yes` has been renamed to `draft init --auto-accept`
* STDIN is now attached when running Draft plugins
* the project file watcher feature has been disabled by default
* fixed a regression where values in draft.toml were not being pushed to the server
* rewrote `draft create` to make charts generated by draft helm-compatible

### Server

* the websocket framework for Draft has been completely re-written to communicate via the gRPC protocol!
* bumped to helm v2.5.1 compatibility
* added `ondraft=true` as an injected value into charts deployed via Draft

### Documentation

* alter project governance to a more team-based model
* add documentation on the new `draft plugins` feature

## v0.5.1

### Client

* fix up --yes being ignored on `draft init`

### Server

* use overlayfs as the selected storage driver

## v0.5.0

### Client

* added .draftignore file support
* added .NET pack support
* added gradle pack support
* renamed java pack as maven
* refactored the PHP and maven packs to utilize multi-stage Dockerfile builds
* re-wrote `draft init` for a smoother installation experience

### Server

* image pull secrets are now updated on changes
* fixed some bugs with running draft on Windows, specifically around `draft home` and `draft create`
* the draft server now runs a docker-in-docker sidecar container instead of mounting the host socket
* bumped to helm v2.5 compatibility

### Documentation

* install documentation has been overhauled with the new `draft init` behaviour
* added project scope
* added project archutecture

### Test Infrastructure

* added codecov integration to new pull requests

## v0.4.0

### Client

* Added -o/--dest flag to `draft create`
* Fixed unused --app flag on `draft create`
* go-bindata is now used to package the default packs, making it easier to contribute new packs

### Server

* Bumped to Helm v2.4 compatibility
* Refactored and cleaned up package `api`

### Documentation

* Added a Draft logo
* Added a nice video tutorial for Draft on Azure Container Services
* Documented `basedomain` and basic ingress setups
* Added descriptions to some of the fields in `draft init`
* Added documentation on getting started with Minikube

### Test Infrastructure

* CI will now publish binaries on tagged releases of Draft

## v0.3.0

### Client

* Added default draft packs for 6 different languages
* Ignore temporary files from file watcher
* Switched to `draft.toml`
* Draft auto-generates the application name on `draft create`

### Server

* Connect to tiller via kubernetes service

### Documentation

* Added example applications for 6 different languages
* Switched getting-started documentation over to use python example app
* Added basedomain logic to ingress hosts
* Added Governance Model

### Test Infrastructure

* Switched to Jenkins
* Upload build artifacts to Azure Blob Storage
* Improved code coverage

## v0.2.0

### Client

* New command: `draft home`
* New command: `draft init`
* Introduced pack detection into `draft create`
* New option flags on `draft up`: `-f`, `--set`, and `--values`
* Introduced a default Ingress resource with the default nginx pack
* Introduced `draft.yaml`

### Server

* Initialized connection to Helm on startup rather than at build time
* Bumped Helm to commit 1aee50f

### Documentation

* Introduced the --watch flag in the Getting Started Guide
* Documented the release process 

### Test Infrastructure

* Introduced Drone CI!
  * Canary images are uploaded to docker registry
  * Canary clients are uploaded to S3 for linux-arm, linux-i386, linux-amd64, darwin-amd64, and windows-amd64
  * Release images and clients are uploaded, too!
* Unit tests for the client and server were improved over this release
* Introduced `hack/docker-make.sh` to run the test suite inside a container

## v0.1.0

Initial release! :tada:
