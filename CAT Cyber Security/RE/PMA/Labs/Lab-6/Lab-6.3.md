1- function `sub_401130` wasn't called in lab-6.2.

![](https://i.imgur.com/t3Rp5rv.png)

2- Two arguments `lpExistingFileName`, `ecx`

![](https://i.imgur.com/H7Hh7we.png)

indicated in function's body as well as they have positive `offset`.

![](https://i.imgur.com/N7d6GAk.png)

3- 
	5 cases `switch` statement with a `jumptable` style.

![](https://i.imgur.com/KPzJsSR.png)


4- Depending on the command it performs one of the following operations:
- creates a folder called `Temp` in `C:\\`

![](https://i.imgur.com/UPU3uDO.png)

-  Drops a file called `cc.exe` in `C:\\Temp`

![](https://i.imgur.com/j2jxiGO.png)

- Edit registry `Software\\Microsoft\\Windows\\CurrentVersion\\Run` with the field `Malware` that has the value `C:\\Temp\\cc.exe`.

![](https://i.imgur.com/ARydyRW.png)

- Delete the dropped `C:\\Temp\\cc.exe` file.

![](https://i.imgur.com/yDr5ivl.png)

- Sleep for a specific duration, `100000`ms in this case.

![](https://i.imgur.com/GjwRh8L.png)

- Finally, default case returns an error that the command wasn't found i.e didn't match any of the cases.

![](https://i.imgur.com/UY2VyQE.png)


5- We can check the following for host-based IOCs
- A folder called `Temp` at `C` drive, `C:\\Temp`.
- A file called `cc.exe` at `C:\\Temp\`.
- Check registry key `Software\\Microsoft\\Windows\\CurrentVersion\\Run` for a field called `malware` with a value of `C:\\Temp\cc.exe`.

6- The purpose of this malware is to read a command from a remote file and based on the command it performs one of the actions, the malware is a dropper that drops `cc.exe` at `C:\\Temp`, it also tries to alter registry key `Software\\Microsoft\\Windows\\CurrentVersion\\Run`.

