1- The `DLL` exports a function named `installer`.

![](https://i.imgur.com/itzAQI9.png)


2- The login found in the disassembly checks for `lab-11-02.ini` and copies `spoolvxx32.dll` to `\` which is the `C` Drive.

![](https://i.imgur.com/gFCAkK5.png)


![](https://i.imgur.com/3goGSFD.png)

However, there are no signs of this action happening on testing machine.

3- It should be in `\` as shown above.

4- The malware adds itself to `AppInit_DLLs` to achieve persistence.

![](https://i.imgur.com/zarj8kr.png)


7- The malware attacks the following process `THEBAT.exe`, `OUTLOOK.exe`, `MSIMN.exe`.

![](https://imgur.com/mZWMpqZ.jpg)



