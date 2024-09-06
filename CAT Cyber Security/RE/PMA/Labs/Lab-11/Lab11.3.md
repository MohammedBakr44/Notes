1- The dll shows some functions used by keyloggers as well as evasion techniques using sleep and Mutex.

![](https://i.imgur.com/xqE2q4f.png)

In the same dll, there's a file named `kernel64x.dll` which can be used as an IoC. also the string `<SHIFT>` supports the claim it's a keylogger.

![](https://i.imgur.com/pmsVc4a.png)

From the `.exe` we can see `cmd.exe` being called and a url `command.com` in the strings, this could be a command and control center of a RAT


![](https://i.imgur.com/WIyQY5t.png)

We can see here `cisvc.exe` and a string to `system32` path, also a suspicious dll with name `inet_epar32.dll`, and the name of the function `zzz69806582` which is exported by the dll.

![](https://i.imgur.com/L95cO5X.png)

4- 


5- A keylogger that writes to a file called `kernel64x.dll` with the format `%s: %s\n` probably as `username: password\n`. It also create a mutex with the name `MZ`.

![](https://i.imgur.com/5ubkSjT.png)

![](https://i.imgur.com/J4tQdXQ.png)


![](https://i.imgur.com/6WD7Yom.png)


![](https://i.imgur.com/cL7ixJi.png)

6- It stores the data in `C:\Windows\System32\Kernel64x.dll`.