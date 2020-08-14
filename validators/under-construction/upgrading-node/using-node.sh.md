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

Before we proceed to next steps we need to download `node.sh` , extract files into the `staging` folder and then move them into the previous folder:

```bash
curl -LO https://harmony.one/node.sh && chmod a+x node.sh
./node.sh -d && mv staging/* ./
```

## 3. Restart Systemd Service

```bash
sudo service harmony restart
```

