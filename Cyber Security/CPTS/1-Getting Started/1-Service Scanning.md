---
share_link: https://share.note.sx/ox97vtxe#cxMVtSCm2qqrc1g7IZvL51zHJjfmQtcVmdEA+nW3GdI
share_updated: 2025-02-18T11:48:16+02:00
---
When we are starting with a target, we need to identify it's OS and services used on it.

Computers are assigned IPs to be to be identifiable and accessible on the internet, *services* running on this server are assigned a port number.

> Port numbers range from **1 to 65,535**, with the range of well-known **ports 1 to 1,023 being reserved for privileged services**. Port 0 is a reserved port in TCP/IP networking and is not used in TCP or UDP messages. If anything attempts to bind to port 0 (such as a service), it will bind to the next available port above port 1,024 because **port 0 is treated as a "wild card" port.**

## Nmap

`nmap {ip_address}` by default scans the most common 1000 ports using TCP.

![](https://i.imgur.com/c17hcEs.png)

> The `STATE` heading confirms that these ports are open. Sometimes we will see other ports listed that have a different state, such as `filtered`. This can happen if a firewall is only allowing access to the ports from specific addresses. The `SERVICE` heading tells us the service's name is typically mapped to the specific port number. However, the default scan will not tell us what is listening on that port. Until we instruct `Nmap` to interact with the service and attempt to tease out identifying information, it could be another service altogether.

**port 3389** is an indication that the target is a windows machine.

`nmap -sC -sV -p-` 
- `-sC` more detailed information.
- `-sV` version scan.
- `-p-` scan all 65,353 ports.

![](https://i.imgur.com/2c74HPU.png)

## Nmap scripts

`nmap --script <script-name> -p<port> <host>`.

example [script](https://raw.githubusercontent.com/cyberstruggle/DeltaGroup/master/CVE-2019-19781/CVE-2019-19781.nse) for `Citrix` [CVE-2019-19781](https://www.rapid7.com/blog/post/2020/01/17/active-exploitation-of-citrix-netscaler-cve-2019-19781-what-you-need-to-know/).

## Banner Grabbing

> banner grabbing is a useful technique to fingerprint a service quickly.

As the service displays a banner once it's connected.

- `nmap -sV --script=banner <target>`
- `nc -nv <target> port`
- `nmap -sV --script=banner -p21 10.10.10.0/24`

## FTP

Previous banner scan revealed that our target uses `vsFTPd 3.0.3`. Also reveals `anonymous authentication` is enabled and a `pub` directory is available.


![](https://i.imgur.com/Dctgcsg.png)

## SMB

> SMB (Server Message Block) is a prevalent protocol on Windows machines that provides many vectors for vertical and lateral movement. Sensitive data, including credentials, can be in network file shares, and some SMB versions may be vulnerable to RCE exploits such as [EternalBlue](https://www.avast.com/c-eternalblue).

`nmap --script smb-os-discovery.nse -p445 <target>` interacts with the target to extract OS version.

![](https://i.imgur.com/Nusum0n.png)


## Shares

> SMB allows users and administrators to share folders and make them accessible remotely by other users. Often these shares have files in them that contain sensitive information such as passwords. A tool that can enumerate and interact with SMB shares is [smbclient](https://www.samba.org/samba/docs/current/man-html/smbclient.1.html). The `-L` flag specifies that we want to retrieve a list of available shares on the remote host, while `-N` suppresses the password prompt.

- `smbclient -N -L \\\\<target>`
- `smbclient \\\\10.129.42.253\\users` to reveal users.

## SNMP

> SNMP Community strings provide information and statistics about a router or device, helping us gain access to it. The manufacturer default community strings of `public` and `private` are often unchanged.


`smbclient -U bob \\\\10.129.42.253\\users` login to user account.

> **In SNMP versions 1 and 2c, access is controlled using a plaintext community string, and if we know the name, we can gain access to it. Encryption and authentication were only added in SNMP version 3.**

[onesixtyone](https://github.com/trailofbits/onesixtyone)

`onesixtyone -c dict.txt 10.129.42.254` brute forcing community strings.

