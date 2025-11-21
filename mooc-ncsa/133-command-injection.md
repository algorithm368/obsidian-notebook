
> [!NOTE] Problem
> read confidential file `/var/www/html/flag_xxxxx.txt` by using command injection

1. enter `localhost` for check if it ping `localhost` then add some syntax like `localhost&ls` from last command you will get flag name
2. get flag by using `localhost&cat${IFS}flagxxxx.txt`