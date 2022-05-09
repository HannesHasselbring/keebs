# Keebs

[Ergogen](ergogen.xyz) generated unibody split Keyboard.
It uses [Task](https://github.com/go-task/task) for build automation

> Currently work in progress

## Keyboards

S1: ![S1](./img/s1.svg)
Uni1: ![Uni1](./img/uni1.svg)


## Getting started

- Clone this repo
- Install [docker](https://www.docker.com/) and [task](https://taskfile.dev/#/installation) make sure to install version min. v3.12.0.
- run `task`

## Build Process

The build process is highly inspired by [Leo B.](https://github.com/soundmonster) Keyboard [samoklava](https://github.com/soundmonster/samoklava).

For PCB routing [freerouting_cli](http://repo.hu/projects/freerouting_cli/) is used. It is compiled with [GraalVM](https://www.graalvm.org/) and dockerized. See [Dockerfile](docker/Dockerfile)


## Inspired by

- [samoklava](https://github.com/soundmonster/samoklava)
- [crkbd](https://github.com/foostan/crkbd)
- [reviung41](https://github.com/gtips/reviung/tree/master/reviung41)
- [Rev-lp](https://github.com/cyril279/keyboards/tree/main/revlp)
- [🐦trochilidae](https://github.com/jcmkk3/trochilidae)
- [absolem](https://github.com/mrzealot/absolem)
- [AA20](https://github.com/choochuwu/AA20)
- [Archimedes Tux Keyboard](https://github.com/Albert-IV/archimedes-tux)
- [truck-n-roll](https://github.com/cacheworks/tuck-n-roll)
