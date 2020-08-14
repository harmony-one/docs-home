# Using Binary CLI

## 1. Backup Files

Backup Node Binary file. Change "`harmony.bkp1`" accordingly to the backup number you are doing:

```bash
mkdir -p backups
cp harmony backups
mv backups/harmony backups/harmony.bkp1
```

The commands above will create a new folder called "`backups`", will copy current `harmony` binary file inside it and rename the file to "`harmony.bkp1".`

## 2. Download Binary CLI

Before we proceed to next steps we need to download the Binary CLI first:

```bash
curl -LO https://harmony.one/binary && mv binary harmony && chmod a+x harmony
```

## 3. Restart Systemd Service

```bash
sudo service harmony restart
```



