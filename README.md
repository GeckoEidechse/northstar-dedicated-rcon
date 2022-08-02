<h1 align="center">northstar-dedicated-rcon</h1>

**RCON version of the Docker image for the [Northstar](https://northstar.tf) dedicated server.** <a href="https://github.com/GeckoEidechse/northstar-dedicated-rcon/actions/workflows/ci.yml"><img src="https://github.com/GeckoEidechse/northstar-dedicated-rcon/actions/workflows/ci.yml/badge.svg?branch=main&event=push" align="right"/></a>

[`ghcr.io/geckoeidechse/northstar-dedicated-rcon:latest`](https://ghcr.io/GeckoEidechse/northstar-dedicated-rcon)

A variation of [pg9182's Docker image](https://github.com/pg9182/northstar-dedicated/) for Northstar that uses the latest version of the [RCON pull request](https://github.com/R2Northstar/NorthstarLauncher/pull/100).

This image is designed mainly for testing the RCON pull request, so using it in production is not recommended!

It is however intended to work as a drop-in replacement for `northstar-dedicated`, simply using a different version of NorthstarLauncher with RCON support tacked on. Therefore instructions on its usage and system requirements can be found in [pg9182's repo](https://github.com/pg9182/northstar-dedicated/).

**Note** that RCON runs over the same port as the gameserver (`37015` by default) but on TCP instead of UDP. As such you need to forward that TCP port as well to access RCON where applicable.

Instructions on RCON usage can be found in its pull request description: https://github.com/R2Northstar/NorthstarLauncher/pull/100

## Usage

1. Replace `ghcr.io/pg9182/northstar-dedicated:1-tf2.0.11.0` with `ghcr.io/geckoeidechse/northstar-dedicated-rcon:latest` in your compose file or Docker command
2. Set a password for RCON that is ≥8 characters long setting it as the value of the `rcon_password` convar
3. RCON always runs on the same port as your gameserver (usually `37015`) but as **TCP** instead of **UDP**, so you will also have to expose that port as tcp in your compose file or Docker command.

## Building

Build image via

```bash
docker build --no-cache -t northstar-dedicated-rcon:latest .
```

## Replacing `pg9182/northstar-dedicated`

As this image is based on pg9182's, it can be used as a drop-in replacement. However as `northstar-dedicated-rcon` does not provide a registry yet, make sure to remove `--pull always` from your run command.
