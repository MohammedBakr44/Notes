Shell is a way to connect to the compromised system.

## Reverse Shell

Most common type of shells; as it's the quickest and easiest method to obtain control over a compromised host.

```
$ nc -lvnp 1234

listening on [any] 1234...
```

We need to get our IP

```
ip a
```

we are interested in `tun0`.

> Note: We are connecting to the IP in 'tun0' because we can only connect to HackTheBox boxes through the VPN connection, as they do not have internet connection, and therefore cannot connect to us over the internet using `eth0`. In a real pentest, you may be directly connected to the same network, or performing an external penetration test, so you may connect through the `eth0` adapter or similar.

The command depends on the OS, refer to [PayloadAllThings](https://swisskyrepo.github.io/InternalAllTheThings/cheatsheets/shell-reverse-cheatsheet/) and [Revshellgen](https://www.revshells.com/.

## Bind Shell

>Another type of shell is a `Bind Shell`. Unlike a `Reverse Shell` that connects to us, we will have to connect to it on the `targets'` listening port.
 
 >Once we execute a `Bind Shell Command`, it will start listening on a port on the remote host and bind that host's shell, i.e., `Bash` or `PowerShell`, to that port. We have to connect to that port with `netcat`, and we will get control through a shell on that system.
 
```
nc <target_ip> <listening_port>  
```

## Updating TTY

```
export TERM=xterm-256color
```

*python one is useless, this is a mediate solution that allows clearing the console and removes the dumb character overlap when pressing tab.*

