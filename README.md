# Docker Clustering en Service Discovery met CoreOS

Presentatie tijdens de DockerGrunn meetup van 3 maart 2015. De [slides staan op Speaker Deck](https://speakerdeck.com/marcelharkema/dockergrunn-20150303-docker-clustering-en-service-discovery-met-coreos).

## Bij aanmaken CoreOS cluster op Digital Ocean...

- Configureer de omgevingsvariabelen `DIGITALOCEAN_TOKEN` en `DIGITALOCEAN_SSH_KEY_NAME`. Zie documentatie van de [Digital Ocean Vagrant provider](https://github.com/smdahlen/vagrant-digitalocean).
- Vergeet niet de discovery URL in digitalocean/user-data aan te passen bij het maken van een nieuw cluster. Zie CoreOS [Cluster Discovery](https://coreos.com/docs/cluster-management/setup/cluster-discovery/) documentatie.

## Deployen

Kopieer de systemd units naar het CoreOS cluster. Gebruik `fleetctl` om te deployen. Zie de [Fleet documentatie](https://coreos.com/docs/launching-containers/launching/launching-containers-fleet/).
