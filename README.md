# Hydra Core

<p align="center">
    <img src="banner.jpg" />
</p>

## Index

1. [Maintainers](#Maintainers)
2. [Introduction](#Introduction)
3. [Contributing](#Contributing)
4. [Documentation](#Documentation)

    - [Developing on Devnet](Developing-on-Devnet)

5. [API Documentation](#API-Documentation)
6. [Credits](#Credits)
7. [License](#License)

## Maintainers

-   [Anfauglith](https://github.com/Anfauglith)
-   [mudlee](https://github.com/mudlee)
-   [wigy](https://github.com/wigy-opensource-developer)

## Introduction

This repository contains the code for the Hydra Blockchain. The Hydra Blockchain is an ARK bridgechain and follows upstream changes as closely as possible.
Changes to naming schemes, documentation and other auxiliary files are thus kept to a minimum. If you want to learn more about the code, check out the original code base at [@ARKEcosystem](https://github.com/ARKEcosystem/core.git).

## Contributing

PRs that are inline with our goals to the core IOP user experience are
more than welcome. To avoid losing precious time you spend on coding, you could
open an issue first and discuss what you are up to before forking and sending us
a PR.

Small note: If editing the README, please conform to the
[standard-readme](https://github.com/RichardLitt/standard-readme) specification.

## Documentation

-   Development : https://docs.ark.io/guidebook/core/development.html
-   Docker : https://docs.ark.io/guidebook/core/docker.html

### Developing on Devnet

#### Prerequisites

The following packages are required before you clone this repository.

1. [Nodejs](https://nodejs.org/en/)
2. [Git](https://git-scm.com/)
3. [Docker](https://www.docker.com/)
4. [Yarn](https://yarnpkg.com/en/)

#### Cloning & Setup for hydra-core repo

```bash
# Clone the hydra core repo.
$ git clone git@github.com:Internet-of-People/hydra-core.git
```

```bash
# Move into the repo and run setup. `setup` hook will install all necessary JavaScript dependencies to get you up and running with hydra ark core.
$ cd hydra-core
$ yarn setup
```

```bash
# Run the following command and it will generate all necessary docker files.
$ yarn docker postgres-hydra
```

```bash
# From core, navigate to `docker/production`. From within this directory, run the following command. This will install Postgres with the necessary settings to work with hydra ark core.
$ docker-compose up -d postgres
```

#### Steps to Setup Devnet

##### Setup Postgres DB

Run the following command. Check that you dont already have a volume setup for `postgres-hydra`.

```bash
docker volumes ls
```

If you don't have `postgres-hydra` module already, set it up using the following command.

```bash
export NETWORK=devnet && export MODE=normal && export FORGING_MODE=no_forge && docker-compose up -d postgres
```

##### Setup Packages

```bash
yarn setup
```

##### Setup Config and Start devnet

This will reset the config and enable you to start the `devnet` with your new configs.

```bash
./packages/core/bin/run config:reset --network=devnet
./packages/core/bin/run relay:run --network=devnet
```

##### Publishing Config

This is used to publish your config changes/

```bash
./packages/core/bin/run config:publish --network=devnet
```

##### Stop and Restart

Use ctrl+c to stop and `./packages/core/bin/run relay:run --network=devnet` to restart.

## API Documentation

-   API v1 : https://docs.ark.io/api/public/v1/
-   API v2 : https://docs.ark.io/api/public/v2/

## Credits

This project exists thanks to all the people who [contribute](../../contributors).

## License

Ark Core is released under the [MIT](LICENSE) © [ARK Ecosystem](https://ark.io)
Changes for Hydra are released under the [MIT](LICENSE) © 2019 Decentralized Society Foundation PA
