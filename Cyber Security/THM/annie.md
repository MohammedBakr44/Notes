Check ssl certificate of a port(get more info)
```sh
openssl s_client -connect <IP>:<PORT>
```

Update shell

```sh
python3 -c 'import pty; pty.spawn("bin/bash")'
export TERM=xterm
```

`ctrl+z`

in main shell:
```sh
stty raw -echo; fg
```


