# DMS in GOLANG

## Intro

This project tries to build a simple document mangement system in golang with a neat web ui for easy usage.
You will be able to access your local folders with your archived documents and search for them.

### Current state

I have a working webapp already build, and iam going to integrate it as soon as possible into this project with a hotreload function for live coding.

### Web UI

Currently we are using the bootstrap templates for the sake of easy and fast development. And they are looking good :) 

### Project / Folder Strcuture

-needs to be edited-

### GO app template build environment

Thanks to thockin for makeing these templates.
We will structure the whole project around this, to get as much as possible into the domain driven development lifecycle.

The below instructions will be modified and more integrated into this project to get a nice workflow.

---

## Run hot reload for coding

1. Install reflex 
    go get github.com/cespare/reflex
2. Run this code inside the folder /cmd/golang-dms/
    reflex -r '\.go' -s -- sh -c "go run ./main.go"

---

# Go app template build environment
[![Build Status](https://travis-ci.org/thockin/go-build-template.svg?branch=master)](https://travis-ci.org/thockin/go-build-template) 

This is a skeleton project for a Go application, which captures the best build
techniques I have learned to date.  It uses a Makefile to drive the build (the
universal API to software projects) and a Dockerfile to build a docker image.

This has only been tested on Linux, and depends on Docker to build.

## Customizing it

To use this, simply copy these files and make the following changes:

Makefile:
   - change `BINS` to your binary name(s)
   - replace `cmd/myapp-*` with one directory for each of your `BINS`
   - change `REGISTRY` to the Docker registry you want to use
   - maybe change `SRC_DIRS` if you use some other layout
   - choose a strategy for `VERSION` values - git tags or manual

Dockerfile.in:
   - maybe change or remove the `USER` if you need

## Go Modules

This assumes the use of go modules (which will be the default for all Go builds
as of Go 1.13) and vendoring (which reasonable minds might disagree about).
You will need to run `go mod vendor` to create a `vendor` directory when you
have dependencies.

## Building

Run `make` or `make build` to compile your app.  This will use a Docker image
to build your app, with the current directory volume-mounted into place.  This
will store incremental state for the fastest possible build.  Run `make
all-build` to build for all architectures.

Run `make container` to build the container image.  It will calculate the image
tag based on the most recent git tag, and whether the repo is "dirty" since
that tag (see `make version`).  Run `make all-container` to build containers
for all supported architectures.

Run `make push` to push the container image to `REGISTRY`.  Run `make all-push`
to push the container images for all architectures.

Run `make clean` to clean up.

Run `make help` to get a list of available targets.
