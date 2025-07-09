
We conduct these tests to find what online systems we can work on in a target.

### Scan Network Range

```shell-session
sudo nmap 10.129.2.0/24 -sn -oA tnet | grep for | cut -d" " -f5
```

- `10.129.2.0/24`: Target Network range.
- `-sn`: Disables port scanning.
- `-oA tnet`: store all results in all formats starting with `tnet`.


```shell-session
nmap -sn -oA tnet -iL hosts.lst | grep for | cut -d" " -f5
```

With a custom list  of IPs `-iL hosts.lst`.

```shell-session
sudo nmap -sn -oA tnet 10.129.2.18 10.129.2.19 10.129.2.20 | grep for | cut -d" " -f5
```

multiple IPs.

```shell-session
sudo nmap -sn -oA tnet 10.129.2.18-20 | grep for | cut -d" " -f5
```

within a range from `10.129.2.18` to `10.129.2.20`.


### Scan Single IP

```shell-session
sudo nmap 10.129.2.18 -sn -oA host -PE --packet-trace
```

 - `-PE`: Performs the ping scan by using 'ICMP Echo requests' against the target.
 - `--packet-trace`: Shows all packets sent and received.


```shell-session
sudo nmap 10.129.2.18 -sn -oA host -PE --reason
```

- `--reason`: display reason for result.

### Host discovery

```
nmap --script smb-os-discovery IPTARGET
```