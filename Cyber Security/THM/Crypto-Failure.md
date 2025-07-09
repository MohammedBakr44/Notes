```sh
$ ffuf -u 'http://<IP>/FUZZ' -w /usr/share/seclists/Discovery/Web-Content/directory-list-2.3-small.txt -e .php,.php.bak -t 100 -mc all -ic -fc 404
```

