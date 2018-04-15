# miskin.fr

## Getting Started

Download Compose and make sure you have the latest version of [Compose](https://docs.docker.com/compose/install/).

Run in the directory:

```
docker-compose up
```

## Architecture

## Networks

The docker stack includes three networks:
* consul.miskin.fr: it includes the consul registry
* secrets.miskin.fr: it includes the vault server
* web.miskin.fr: it includes the traefik and all the services

## Services

### Consul

Consul is used as backend storage for Vault server

### Vault

Vault must be initiated at its first usage. Enter the container with the following command:

```
docker exec -it miskinfr_vault_1 sh
```

initiate vault with a number of key shares and key thresolds. For example, with 5 key shares and 2 key threshold:

```
vault operator init -key-shares=5 -key-threshold=2
```

Obtained keys and the root token MUST be stored securly.
The vault can be latter unsealed by succesively executing the `vault unseal` command with a number of key threshold. 

### Vault-ui

A web interface that can be use to manage vault content is exposed.

### Traefik




