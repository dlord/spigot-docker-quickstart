# Spigot-BungeeCord-on-Docker Quickstart

* * *


## Prerequisites

You must have Docker and Docker Compose installed. This has been tested against
Docker 1.9 and Docker Compose 1.5.2.

To install Docker and Docker Compose, please follow the [official guide][].


## Instructions

**It is highly recommended to fork this repo.**

After cloning the repository, deploy the whole stack by running the following:

    docker-compose up -d

This will launch BungeeCord, Spigot, and a MySQL DB instance. Spigot includes
CoreProtect, and has been preconfigured to work with the dockerized MySQL DB
instance.

By default, this server is locked down. You will need to add yourself to the
whitelist either by attaching to the Spigot console (via `docker attach`), or
by using the scripting capability of the `dlord/spigot` docker image. See
the [Scripting][] section of the `dlord/spigot` README for details.

You can now connect to the server via port `25577`

By default, this runs BungeeCord and Spigot in "development mode". The default
configuration is located in `docker-compose.override.yml`. You may customize
this file to your liking.

The recommended approach to customize the docker compose configuration is to
create a separate configuration per environment
(e.g. `docker-compose.production.yml`). You may use the contents of
`docker-compose.override.yml` as basis.

To use your customized configuration, run the following:

    docker-compose \
        -f docker-compose.yml \
        -f docker-compose.production.yml \
        up -d

For more details, please see the [Different environments][] section of the
Docker Compose documentation.


## Database Security

It is highly recommended to change the database passwords set in
`docker-compose.override.yml`. You will also need to update the database
password declared in `spigot/plugins/CoreProtect/config.yml`.


## Pull Request Guidelines

All pull requests must have a description, and commit messages must follow
the Linux Kernel standards. Please see [Care And Operation Of Your Linus Torvalds][]
or [How to Write a Git Commit Message][] by Chris Beams.

Pull requests will be rejected if they do not follow these guidelines.


[official guide]: https://docs.docker.com/compose/install/
[Scripting]: https://github.com/dlord/spigot-docker#scripting
[Different environments]: https://docs.docker.com/compose/extends/#different-environments
[Care And Operation Of Your Linus Torvalds]: https://www.kernel.org/doc/Documentation/SubmittingPatches
[How to Write a Git Commit Message]: http://chris.beams.io/posts/git-commit/
