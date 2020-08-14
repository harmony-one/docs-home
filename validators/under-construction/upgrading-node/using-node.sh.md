# Using Node.sh

## 1. Stop Systemd Service

```bash
sudo service harmony stop
```

## 2. Backup Files

Create a folder called "`backup`" in case it does not exist:

```bash
mkdir -p backup
```

Backup both `node.sh` and `harmony` binary file:

```bash
cp {node.sh,harmony} backup
```

## Download Node.sh

```bash
curl -LO https://harmony.one/node.sh && chmod a+x node.sh
./node.sh -d && mv staging/* ./
```

## 3. Restart Systemd Service

```bash
sudo service harmony restart
```

