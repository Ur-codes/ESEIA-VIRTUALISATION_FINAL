# ESEIA-VIRTUALISATION
# HumansBestFriend app? CATs or DOGs ?

A simple distributed application running across multiple Docker containers only for linux OS on this version.

## Requirement

- The project need to be done inside a virtual machine that run docker and docker compose. Follow the docker documentation as we saw during the course for installation instructions if you don't have it yet.

- Please rename your project folder like these : esiea

If you not do this, it will cause some problem for build the app

- Make sure you install docker & docker compose before you start !


For docker :
- https://docs.docker.com/engine/install/ubuntu/
- https://docs.docker.com/engine/install/linux-postinstall/
- https://docs.docker.com/compose/install/

For docker compose :
```shell
sudo curl -SL https://github.com/docker/compose/releases/download/v2.23.3/docker-compose-linux-x86_64 -o /usr/local/bin/docker-compose
```

To add local images (worker/result/vote) to your docker, be on your directory to build the app and execute this command :
```shell
docker compose build
```

## Getting started

This solution uses Python, Node.js, .NET, with Redis for messaging and Postgres for storage.

Be on your directory and run the app:

```shell
docker compose up
```

The vote app will be running at http://localhost:5002, and the results will be at http://localhost:5001.

To close the app:

```shell
docker compose down
```

## Architecture

![Architecture diagram](architecture.png)

- A front-end web app in [Python](/vote) which lets you vote between two options
- A [Redis](https://hub.docker.com/_/redis/) which collects new votes
- A [.NET](/worker/) worker which consumes votes and stores them in…
- A [Postgres](https://hub.docker.com/_/postgres/) database backed by a Docker volume
- A [Node.js](/result) web app which shows the results of the voting in real time

## Notes

The `HumansBestFriend` application only accepts one vote per client browser. It does not register additional votes if a vote has already been submitted from a client.

This isn't an example of a properly architected perfectly designed distributed app... it's just a simple
example of the various types of pieces and languages you might see (queues, persistent data, etc), and how to
deal with them in Docker at a basic level.

# Submission

- You need to fork this project to your own public github repository
- You need to submit your own public github repository with the required files (`Dockerfile`, `compose.yml`, `docker-compose.build.yml` etc....).
- Deploy the app first using docker compose
- This need to be in a team of 3 MAXIMUM. No single submission is allowed. Please do not use docker desktop to do the job
- Take all the necessary screenshots that will showcase your work
- The moodle is `G-47`. You need to submit before the deadline.
- Make sure your team members name is visible inside your pdf file

### Usefull links

- https://kubernetes.io/docs/setup/production-environment/tools/
- https://docs.docker.com/engine/install/ubuntu/
- https://docs.docker.com/compose/gettingstarted/
- https://kubernetes.io/docs/reference/kubectl/cheatsheet/
