# Upgrade

The Bitcoin bridge is in beta stage and throughout the first couple of months, the bitcoin bridge team may upgrade the vault client software to make it more efficient and improve the UX. This guide will help to keep your vault client up to date.

#### Steps

1. Stop the docker container

```
docker-compose down
```

2\. Re-download the script

```
rm docker-compose.yaml
curl -L -o 'docker-compose.yml' https://raw.githubusercontent.com/harmony-one/onebtc.relayer-client/main/docker-compose.yml
docker-compose pull
```

3\. Restart the container

```
docker-compose up -d
```
