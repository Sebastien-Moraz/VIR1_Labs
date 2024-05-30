# Labo04 - A first stateless microservice

## Pedagogical intent

This lab will certainly be a little more complex than the previous ones, but it's excellent preparation for the rest of the module project.

Here are the skills trained:
* Discover spring MVC architecture for REST api backend applications,
* Deploying a 2-tier application in Docker using a DockerCompose file,
* Use input parameters to launch containers,
* Test api calls to your Dockerized application via curl.

## Backlog

### Initial setup
* Clone this repository

```
git clone https://github.com/CPNV-VIR1/spring-rest-api.git
```

* Read the readme

* Deploy the app

* Test the app (manually)

### Docker setup

* Init docker

[INPUT]
```
docker init
```

[OUTPUT]
```
Welcome to the Docker Init CLI!

This utility will walk you through creating the following files with sensible defaults for your project:
  - .dockerignore
  - Dockerfile
  - compose.yaml
  - README.Docker.md

Let's get started!

? What application platform does your project use?  [Use arrows to move, type to filter]
  Java - (detected) suitable for a Java application that uses Maven and packages as an uber jar
  Go - suitable for a Go server application
  Python - suitable for a Python server application
  Node - suitable for a Node server application
  Rust - suitable for a Rust server application
  ASP.NET Core - suitable for an ASP.NET Core application
  PHP with Apache - suitable for a PHP web application
  Other - general purpose starting point for containerizing your application
  Don't see something you need? Let us know!
> Quit
```

### Deploy the app with Docker and data Persistence

[Source](https://docs.docker.com/language/java/develop/)

