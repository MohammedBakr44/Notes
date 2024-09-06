1- It stores the name of a process after decoding(?) it and then opens that process.

![](https://i.imgur.com/ASxWwM2.png)


2 - The injected process is `\\system32\wupdmgr.exe` and the malware drops the file `\\winup.exe`.

![](https://i.imgur.com/ZX5FSbZ.png)


3- `psapi.dll`.

![](https://i.imgur.com/yLHZIyz.png)

and `sfc_os.dll`

![](https://i.imgur.com/gMOdoFU.png)


4- Start Address of the thread.

![](https://i.imgur.com/ZoevXoV.png)

5, 6- The first malware performs loads a binary from `resources` section and performs privilege escalation as we can see from some imports.

![](https://i.imgur.com/oYSyIBY.png)


The dropped binary is a `Downloader` that downloads file `updater.exe` from `practicalmalwareanalysis.com`

![](https://i.imgur.com/9I7V4CH.png)

![](https://i.imgur.com/l6kezpL.png)