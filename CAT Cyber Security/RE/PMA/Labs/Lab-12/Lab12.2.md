2- The program uses `DLL Injection`, which we can see in these snippets from `sub_4010EA`.

![](https://i.imgur.com/MmZXmQ7.png)

![](https://i.imgur.com/Ns5rXhf.png)

![](https://i.imgur.com/WRuU16e.png)


3- The payload is stored in resources section, in an encrypted/obfuscated form, we can see that the sample utilises some resources related functions such as `LoadResource`, `SizeofResource` and `_memcpy`.

![](https://i.imgur.com/yGYFvJD.png)


![](https://i.imgur.com/zZCFtov.png)

![](https://i.imgur.com/Q4giUpG.png)


4- The payload is encrypted/obfuscated in the resources section.