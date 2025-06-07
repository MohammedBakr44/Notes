## Spoofing user-agent

```bash
curl -A "<content>" -L $IP
```

- `-A` spoof user-agent.
- `-L` follow all redirects.

## hash cracking

```bash
hydra -l <username> -P <wordlist> $IP <service>
```

## Steg

```bash
binwalk <file>
```

- check for files hidden in other files.

```bash
binwalk -e <file>
```

- extract hidden files.

```bash
zip2john <file>.zip > zip.hash
```

- extract zip file hash for john to brute-force.

```bash
john zip.hash
```

- start brute-forcing the password.

```bash
steghide info <file>
```

- check hidden files.

```bash
steghide extract -sf <file>
```

- extract hidden files.

