# Using Binary CLI

## 1. Backup Files

Create a folder called "`backup`" in case it does not exist:

```bash
mkdir -p backup
```

Backup the `harmony` binary file:

```bash
cp harmony backup
```

## 2. Download Binary CLI

Before we proceed to next steps we need to download the Binary CLI first:

```bash
curl -LO https://harmony.one/binary && mv binary harmony && chmod a+x harmony
```

## 3. Restart Systemd Service

```bash
sudo service harmony restart
```



