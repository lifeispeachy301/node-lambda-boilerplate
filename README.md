# Node Lambda Boilerplate

This project aims to provide developers with a quick start local node AWS lambda environment using the work done over at [lambci/docker-lambda](https://github.com/lambci/docker-lambda).

## Getting Started ##

All you need to get started is [Docker](https://www.docker.com/products/overview)!

## Installation

Clone this project into a new working directory on your machine.

```sh
$ git clone git@github.com:lifeispeachy301/node-lambda-boilerplate.git my-new-lambda-project
```

## Usage

Once cloned you should add any dependencies your project might need to `package.json`. Extra dependencies can always be installed later.

then,
```
$ docker-compose up
```

The result is a long running docker container that emulates AWS lambda exuting your function.
The container does the following:

  1. installs npm packages against the correct environment
  2. wraps the function call in nodemon so that your function re-runs when code changes are made
  3. exposes packages that are useful to deploying test functions directly from your machine (aws-cli, zip)

## Warning ##

The resulting image has extra packages added to it that will not be present in the production lambda environment. You should still test your function with the images over at
[lambci/docker-lambda](https://github.com/lambci/docker-lambda).

particularly `lambci/lambda` to run tests and `lambci/lambda:build` to build your npm packages


## TODO ##

* give examples of how to install extra npm packages after the fact
* give example of how to zip dir and update a lambda function with aws-cli
* list extra installed packages
* come up with an easier way to pass test json to lambda
* add build and test commands to npm scripts



