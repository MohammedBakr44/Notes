---
share_link: https://share.note.sx/yawd255f#J6NeJYE1Xeqvy7O7c+QEPrAmA/j3ERgCplBMheWZfAA
share_updated: 2025-02-20T17:27:08+02:00
---

When given initial access, we start looking for vulns to gain root access, as root is the most privileged user in Linux systems.

## Resources
- [Hacktricks checklist](https://book.hacktricks.wiki/en/linux-hardening/linux-privilege-escalation-checklist.html)
- [Notes by C3rb3rus](https://zyadelsayed.notion.site/Linux-privilege-escalation-fa5565e3861e4c8a94541f109bd96ed5)
- [gtfo bins](https://gtfobins.github.io/)
## Automated scripts
### Linux
- [LinEnum](https://github.com/rebootuser/LinEnum)
- [linuxprivchecker][https://github.com/sleventyeleven/linuxprivchecker]
- [LinPeas](https://github.com/peass-ng/PEASS-ng/tree/master/linPEAS)
### Windows
- [Seatbelt](https://github.com/GhostPack/Seatbelt)
- [Jaws](https://github.com/411Hall/JAWS)
- [Winpeas](https://github.com/peass-ng/PEASS-ng/tree/master/winPEAS)

## Kernel Exploits

Very simple, just run `uname -a` or `cat /proc/version` and google kernel version + CVE, transfer the exploit file and boom you `pwn'd`.

## Vulnerable software 

Same as Kernel, run `dpkg -l` and look for potential vulnerable programs that allows read/write file, or even spawn a shell as root. We can use `gtfo bins` to find payloads.


## User Privs

We start by running `sudo -l` and look for programs with `NOPASSWD` access.
e.g:

```
sudo -l

(user : user) NOPASSWD: /bin/echo
```

we can then use this program to perform `lateral movement`.

```
sudo -u user /bin/echo Hello World!
```

depending on the result we can use any of `gtfo` payloads to gain root access.

### Example
In the case in the exercise of this section, the following was returned

```
sudo -l
(user2 : user2) NOPASSWD /bin/bash
```

which allowed us to spawn another bash as user2 and giving us the flag.

## Scheduled Tasks

In some cases we have access to edit the list of `cron` jobs, we can use that to execute a custom payload.

`cron` files include:
- `/etc/crontab`
- `/etc/cron.d`
- `/var/spool/cron/crontabs/root`

*more on this later if I decided to writeup THM linux privesc room*

## Exposed Credentials

`Exposed Credentials` in config files(e.g: database files), `.bash_history`. we can also check for *passowrd reuse*.


## SSH Keys

Sometimes our user can have read/write access on `~/.ssh` folder, depending on the case we can use that to initiate a connection from our end.

- [READ ACCESS] Obtaining a private key file
```
chmod 600 id_rsa
ssh root@<target_ip> -i id_rsa
```

- [WRITE ACCESS] we can add our public key to `~/.ssh/authorized_keys`, if we did this we can connect easily without any form authentication.

